#include <stdio.h>
#include <math.h>

// Function to calculate factorial
unsigned long long factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}

// Function to calculate the Poisson likelihood function
double poissonLikelihood(int k, double lambda) {
    return (exp(-lambda) * pow(lambda, k)) / factorial(k);
}

int main() {
    int n; // Number of observations
    printf("Enter the number of observations: ");
    scanf("%d", &n);

    int data[n]; // Array to store the observed data

    printf("Enter the observed data:\n");
    for (int i = 0; i < n; i++) {
        printf("Data %d: ", i + 1);
        scanf("%d", &data[i]);
    }

    double sum = 0;
    for (int i = 0; i < n; i++) {
        sum += data[i];
    }

    double lambda = sum / n; // Maximum Likelihood Estimate

    printf("MLE estimate of lambda (intensity): %lf\n", lambda);

    return 0;
}
