# my-first-repository
// C++ program to count ways to write 
// 'n' as sum of digits 
#include<iostream.h> 


// Function to count 'num' as sum of 
// digits(1, 2, 3, 4) 
int countWays(int num) 
{ 
	// Initialize dp[] array 
	int dp[num+1]; 

	const int MOD = 1e9 + 7; 
	// Base case 
	dp[1] = 2; 

	for(int i = 2; i <= num; ++i) 
	{ 
		// Initialize the current dp[] 
		// array as '0' 
		dp[i] = 0; 

		for(int j = 1; j <= 3; ++j) 
		{ 
			/* if i == j then there is only 
			one way to write with element 
			itself 'i' */
			if(i - j == 0) 
			dp[i] += 1; 

			/* If j == 1, then there exist 
			two ways, one from '1' and 
			other from '4' */
			else if (j == 1) 
			dp[i] += dp[i-j] * 2; 

			/* if i - j is positive then 
			pick the element from 'i-j' 
			element of dp[] array */
			else if(i - j > 0) 
			dp[i] += dp[i-j]; 

		// Check for modulas 
		if(dp[i] >= MOD) 
			dp[i] %= MOD; 
		} 

	} 

	// return the final answer 
	return dp[num]; 
} 


// Driver code 
int main() 
{ 
	int n = 3; 
	cout << countWays(n); 
	
	return 0; 
} 

