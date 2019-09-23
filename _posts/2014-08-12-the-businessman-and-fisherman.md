---
layout: post
cover: 'assets/images/cover7.jpg'
navigation: True
title: Generating $\pi$ from the prime numbers
date: 2019-09-09
tags: prime numbers number theory
subclass: 'post tag-test tag-content'
logo: 'assets/images/ghost.png'
author: Aymen Hafeez
categories: Mathematics
---

<br><br>
At first glance the prime numbers seem randomly distributed along the numberline. Even at the second, third and fourth glance it would be difficult to say that there is some obvious pattern there. However, working with the Riemann zeta function shows that this is far from true. One of my favourite results stemming from the Riemann zeta function is deriving an expression to approximate $\pi$ using the prime numbers. This is quite an astounding result considering the various equations and models in which $\pi$ shows up. At the core of this derivation is Euler's product formula which relates the Riemann zeta function to the prime numbers:

  $$\zeta(s)=\sum_{n=1}^{\infty} \frac{1}{n^s} = \prod_{p \ \text{prime}} \frac{1}{1-p^{-s}}$$ 

I plan on doing a separate post dedicated to Euler which will detail a proof of this formula. 

We must first begin by deriving the following general expression for the Riemann zeta function over the even positive integers:

  $$\zeta(2k)=\frac{(-1)^{k+1}(2\pi)^{2k}\beta_{2k}}{2(2k!)}$$

$\beta_{2k}$ are the even valued Bernoulli numbers. This derivation is not completely required to appreciate the result at the end, so it can be skipped. However, I recommend going through it because it's fun.

We start by expressing function $\frac{\sin(\pi x)}{\pi x}$ in its infinite product form:

  $$\frac{\sin(\pi x)}{\pi x}=\prod_{n=1}^{\infty}\left(1-\frac{x^2}{n^2}\right)$$
 
A way of understanding this representation is by realising that $\frac{\sin(\pi x)}{\pi x}$ can be expressed as a product of linear factors, as you would with any other polynomial. Let us consider the following polynomial as an example:  

  $$f(x)=x^2+7x+12$$ 

We know that it can be expressed as a product of its linear factors:  

  $$f(x)=(x+4)(x+3)$$

However, it can also be expressed as  

  $$f(x)=\left(1+\frac{x}{4}\right)\left(1+\frac{x}{3}\right)$$

This can be verified by seeing that $f(-4)$ and $f(-3)=0$. However, look into the Weierstrass factorisation theorem for a more rigorous explanation on expressing functions in this form.
  
<!--<center> <img src="/assets/images/sincpi.png" width="700" height="350" > </center>-->
  
$\frac{\sin(\pi x)}{\pi x}$ has roots at $x=n$ for $n \in \mathbb{Z}$ and $n \neq 0$, and so, expressing it as a product of its linear factors in a similar way gives
  
  $$\frac{\sin(\pi x)}{\pi x}=\left(1-x\right)\left(1+x\right)\left(1-\frac{x}{2}\right)\left(1+\frac{x}{2}\right)\left(1-\frac{x}{3}\right)\left(1+\frac{x}{3}\right)\cdots$$
  
Making the observation that each pair of terms is the difference of two sqaures, multiplying each pair together gives the infinite product form:

  $$\frac{\sin(\pi x)}{\pi x}=\left(1-x^2\right)\left(1-\frac{x^2}{4}\right)\left(1-\frac{x^2}{9}\right)\cdots$$
  
We can now begin deriving the equation we set out to find. The first step is to manipulate Equation (3) to a point where we recognise something of the sort we are trying to derive. Let us first take the natural logarithm of both sides of Equation (3):
  
  $$\log{\frac{\sin(\pi x)}{\pi x}}=\log\left(\prod_{n=1}^{\infty}\left(1-\frac{x^2}{n^2}\right)\right)$$

Making use of the property that the logarithm of a product is equivalent to the sum of the individual logarithms gives

  $$\log{\frac{\sin(\pi x)}{\pi x}}=\sum_{n=1}^{\infty}\log{\left(1-\frac{x^2}{n^2}\right)}$$  
  
  $$\log{(\sin(\pi x))}=\log{(\pi x)}+\sum_{n=1}^{\infty}\log{\left(1-\frac{x^2}{n^2}\right)}$$  

Taking the derivative of both sides:

  $$\frac{d}{dx}\left[\log{(\sin(\pi x))}\right]=\frac{d}{dx}\left[\log{(\pi x)}+\sum_{n=1}^{\infty}\log{\left(1-\frac{x^2}{n^2}\right)}\right]$$  
  
  $$\frac{\pi \cos(\pi x)}{\sin(\pi x)}=\frac{1}{x}-\sum_{n=1}^{\infty}\left(\frac{2x}{n^2}\right)\left(\frac{1}{1-\frac{x^2}{n^2}}\right)$$  
  
  $$\pi x \cot(\pi x)=1-2\sum_{n=1}^{\infty}\left(\frac{x^2}{n^2}\right)\left(\frac{1}{1-\frac{x^2}{n^2}}\right)$$  

The $\frac{1}{1-\frac{x^2}{n^2}}$ term can be expressed as a Taylor series exapansion, giving

  $$\pi x \cot(\pi x)=1-2\sum_{n=1}^{\infty}\sum_{k=0}^{\infty}\left(\frac{x^2}{n^2}\right)\left(\frac{x^2}{n^2}\right)^k$$
  
  $$\pi x \cot(\pi x)=1-2\sum_{n=1}^{\infty}\sum_{k=0}^{\infty}\left(\frac{x^2}{n^2}\right)^{k+1}$$

The lower limit of the inner summation can be changed to $k=1$ if we also change the exponent of the term being summed:

  $$\pi x \cot(\pi x)=1-2\sum_{n=1}^{\infty}\sum_{k=1}^{\infty}\frac{x^{2k}}{n^{2k}}$$

  $$\pi x \cot(\pi x)=1-2\sum_{k=1}^{\infty}\zeta(2k)x^{2k}$$

And so, we see that we have some sort of expression with $\zeta(2k)$ on the right-hand side. Let us now take a closer look at the cotangent function on the left-hand side.
  
The cotangent can be expressed as the ratio of cosine to sine. Expressing the cosine and sine in their exponential function form gives

  $$\pi x \cot(\pi x)=\pi x\frac{\cos(\pi x)}{\sin(\pi x)}=\pi x \frac{e^{i\pi x}+e^{-i\pi x}}{2}\frac{2i}{e^{i\pi x}-e^{-i\pi x}}$$
  
  $$\pi x \cot(\pi x)=i\pi x \frac{e^{i\pi x}+e^{-i\pi x}}{e^{i\pi x}-e^{-i\pi x}}$$

The next step requires a couple of neat tricks. Multiplying the right-hand by $\frac{e^{i\pi x}}{e^{i\pi x}}$:

  $$\pi x \cot(\pi x)=i\pi x \frac{e^{i\pi x}+e^{-i\pi x}}{e^{i\pi x}-e^{-i\pi x}} \cdot \frac{e^{i\pi x}}{e^{i\pi x}}$$
  
  $$\pi x \cot(\pi x)=i\pi x \frac{e^{2i\pi x}+1}{e^{2i\pi x}-1}$$

And now, splitting the numerator, we get

  $$\pi x \cot(\pi x)=i\pi x \frac{e^{2i\pi x}-1+2}{e^{2i\pi x}-1}$$
  
  $$\pi x \cot(\pi x)=i\pi x \left(1+\frac{2}{e^{2i\pi x}-1}\right)$$
  
  $$\pi x \cot(\pi x)=i\pi x+\frac{2i\pi x}{e^{2i\pi x}-1}$$

Those last couple of steps may have seemed unintuitive (because they were). However, they served the purpose of getting the expression into a specific form, namely so that we can get the Bernoulli numbers involved. We can do this by making use of the following:

  $$\frac{x}{e^x-1}=\sum_{k=0}^{\infty}\frac{\beta_k}{k!}x^k$$
 
 Substituting this into Equation (25) we get
 
   $$\pi x \cot(\pi x)=i\pi x+\sum_{k=0}^{\infty}\frac{\beta_k}{k!}(2i\pi x)^k$$
 
Now - this should look familiar. It looks quite similar to Equation (18):

  <center> $\pi x \cot(\pi x)=1-2\sum_{k=1}^{\infty}\zeta(2k)x^{2k}$ </center>

We have another expression for $\pi x \cot(\pi x)$. On the right-hand side we have an expression in with respect to $x^k$, whereas Equation (18) is in terms of $x^{2k}$. We can manipulate the above equation to get it into a form such that it can be equated to Equation (18), and by comparing coeffiecients of $x$ we can get an expression for $\zeta(2k)$. 

Let us begin by expanding out the first two terms of the summation:

  $$\pi x \cot(\pi x)=i\pi x+\frac{\beta_0}{0!}+\frac{\beta_1}{1!}(2i \pi x)+\sum_{k=2}^{\infty}\frac{\beta_k}{k!}(2i\pi x)^k$$

$\beta_0=1$ and $\beta_1=-\frac{1}{2}$, and so we get

  $$\pi x \cot(\pi x)=i\pi x+1-\frac{1}{2}(2i \pi x)+\sum_{k=2}^{\infty}\frac{\beta_k}{k!}(2i\pi x)^k$$
  
  $$\pi x \cot(\pi x)=1+\sum_{k=2}^{\infty}\frac{\beta_k}{k!}(2i\pi x)^k$$

We can see that we are getting very close to our desired result. At this point it is just a case of manipulating the expression to get it into the desired form.

  $$\pi x \cot(\pi x)=1-2\sum_{k=2}^{\infty}\frac{\beta_k}{k!}\frac{(2i\pi x)^k}{-2}$$
  
We can alter the lower summation limit by correcting the exponent:

  $$\pi x \cot(\pi x)=1-2\sum_{k=1}^{\infty}\frac{\beta_{2k}}{2k!}\frac{(2i\pi x)^{2k}}{-2}x^{2k}$$
  
  $$\pi x \cot(\pi x)=1-2\sum_{k=1}^{\infty}\frac{i^{2k}(2\pi)^{2k}\beta_{2k}}{-2(2k!)}x^{2k}=1-2\sum_{k=1}^{\infty}\frac{(-1)^{k}(2\pi)^{2k}\beta_{2k}}{-2(2k!)}x^{2k}$$

And so, we get

  $$\pi x \cot(\pi x)=1-2\sum_{k=1}^{\infty}\frac{(-1)^{k+1}(2\pi)^{2k}\beta_{2k}}{2(2k)!}x^{2k}$$

Finally, we can equate the right-hand side of the above equation to that of Equation (18) to get

  $$\zeta(2k)=\frac{(-1)^{k+1}(2\pi)^{2k}\beta_{2k}}{2(2k)!}$$

This was a very dense proof, but the ultimate goal was to relate $\pi$ to the prime numbers. Plugging Equation (35) into Euler's product formula gives the following:

  $$\zeta(2k)=\frac{(-1)^{k+1}(2\pi)^{2k}\beta_{2k}}{2(2k)!}=\prod_{p \ \text{prime}} \frac{1}{1-p^{-2k}}$$

Let us consider the case for $k=1$. We get

  $$\zeta(2)=\frac{(-1)^2(2\pi)^2\beta_2}{2(2)}=\prod_{p \ \text{prime}} \frac{1}{1-p^{-2}}$$
  
  $$\frac{\pi^2}{6}=\prod_{p \ \text{prime}} \frac{1}{1-p^{-2}}$$

(Note: this is the solution to the Basel problem, which we will look at in more detail in another post). And so, rearranging for $\pi$ gives

  $$\pi=\sqrt{6\prod_{p \ \text{prime}} \frac{1}{1-p^{-2}}}$$

As $k$ can take an infinite number of values there are an infinite number of relations which can be made! The general expression can be given as

  $$\frac{(-1)^{k+1}(2\pi)^{2k}\beta_{2k}}{2(2k!)}=\prod_{p \ \text{prime}} \frac{1}{1-p^{-2k}}$$
  
  $$\pi=\frac{1}{2}\sqrt[2k]{\frac{2(2k)!}{(-1)^{k+1}\beta_{2k}}\prod_{p \ \text{prime}} \frac{1}{1-p^{-s}}}$$

I know this looks messy, but let us put some more values of $k$ into the above equation:

* $k=2 \rightarrow \pi=\frac{1}{2}\sqrt[4]{1440\prod_{p} \frac{1}{1-p^{-4}}}$
* $k=3 \rightarrow \pi=\frac{1}{2}\sqrt[6]{60480\prod_{p} \frac{1}{1-p^{-6}}}$
* $k=4 \rightarrow \pi=\frac{1}{2}\sqrt[8]{2419200\prod_{p} \frac{1}{1-p^{-8}}}$

Is this not one of the coolest things you have ever seen? Let's take a look at the convergence.
<!--
<center>
<figure> 
  <img src="/assets/images/prime1.gif" width="650" height="300"/> 
  <figcaption>$k=1$</figcaption> 
</figure>
-->
<!-->
<figure> 
  <img src="/assets/images/prime2.gif" width="650" height="300"/> 
  <figcaption>$k=2$</figcaption> 
</figure>
-->
<!--
<figure> 
  <img src="/assets/images/prime3.gif" width="650" height="300"/> 
  <figcaption>$k=3$</figcaption> 
</figure> 
-->
<!--
<figure> 
  <img src="/assets/images/prime4.gif" width="650" height="300"/> 
  <figcaption>$k=4$</figcaption> 
</figure> 
</center>
-->
The plots show that as $k$ increases the expression converges faster. Let us take another look at the exression for $\pi$ for $k=1$.

  $$\pi=\frac{1}{2}\sqrt{24\prod_{p \ \text{prime}} \frac{1}{1-p^{-2}}}$$

If we separate the $\sqrt{24}$ from the root of the product we get

  $$\pi=\frac{\sqrt{24}}{2}\sqrt{\prod_{p\ \text{prime}} \frac{1}{1-p^{-2}}}$$

We see that the constant $\frac{\sqrt{24}}{2}\simeq2.449$. This does not seem like a particularly special number. However, let us do the same for $k=2$:
  
  $$\pi=\frac{\sqrt{1440}}{2}\sqrt[4]{\prod_{p\ \text{prime}} \frac{1}{1-p^{-4}}}$$

The constant in this case, $\frac{\sqrt{1440}}{2}\simeq3.080$. Still perhaps nothing really noteworthy, but bear with me. Again, for $k=3$ and $k=4$ the constants are $\frac{\sqrt[6]{60480}}{2}\simeq3.133$ and $\frac{\sqrt[8]{2419200}}{2}\simeq3.140$. The constants seem to be approaching $\pi$. Considering where this constant comes from we see from Equation (41) that these constants, which we shall call $p_k$, have the general form

  $$p_k=\frac{1}{2}\sqrt[2k]{\frac{2(2k)!}{(-1)^{k+1}\beta_{2k}}}$$

And for $k=5$ and $k=10$,  $p_5\simeq3.14128$ and $p_{10}\simeq3.141592504$. Now this is interesting. And so, it would seem that

  $$\lim_{k\to\infty} \frac{1}{2}\sqrt[2k]{\frac{2(2k)!}{(-1)^{k+1}\beta_{2k}}}=\pi$$

and

  $$\lim_{k\to\infty} {\prod_{p\ \text{prime}} \frac{1}{1-p^{-2k}}}=1$$


<!--more-->
