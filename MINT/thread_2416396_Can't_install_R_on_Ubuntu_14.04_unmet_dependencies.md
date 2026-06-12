---
title: "Can't install R on Ubuntu 14.04: unmet dependencies"
date: 2019-04-09
forum: MINT
---

### Post by oktu on 2019-04-09
I use Linux Mint 17.2 Rafaela Ubuntu 14.04.6 LTS

I try to install R 3.0.1.

I run:

```


sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu trusty-cran35/"
sudo apt-get update
sudo apt-get install r-base
```
And I get the problem:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 r-base : Depends: r-recommended (= 3.5.3-1trusty) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

How I can fix it?

---

### Post by deadflowr on 2019-04-09
*Thread moved to **MINT***

---

### Post by huff2 on 2019-04-09
R 3.5 packages from that repository are not supported for you Ubuntu release. See the following statement from that repositories README file:

'''
R 3.5 packages for Ubuntu on i386 and amd64 are available for most stable Desktop releases of Ubuntu until their official end of life date. However, only the latest Long Term Support (LTS) release is fully supported.  As of November 18, 2018 the supported releases are Xenial Xerus (16.04; LTS), Trusty Tahr (14.04; LTS), Bionic Beaver (18.04;LTS), and Cosmic Cuttlefish (18.10).  Note, to install R 3.5 packages, a different sources.list entry is needed.  See below for details.

R 3.4 packages for Ubuntu on i386 and amd64 are available for all stable Desktop releases of Ubuntu prior to Bionic Beaver (18.04) until their official end of life date. However, only the latest Long Term Support (LTS) release is fully supported.  As of November 18, 2018 the supported releases are Xenial Xerus (16.04; LTS), and Trusty Tahr (14.04; LTS).

See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) for details.

For additional binary packages for R (currently 4,000+), check out the CRAN2deb4ubuntu PPA: [https://launchpad.net/~marutter/+archive/ubuntu/c2d4u](https://launchpad.net/~marutter/+archive/ubuntu/c2d4u) or [https://launchpad.net/~marutter/+archive/ubuntu/c2d4u3.5](https://launchpad.net/~marutter/+archive/ubuntu/c2d4u3.5) depending on which version of R you are using.
'''

This is probably your problem.

The output you have confirms the issue is that your Ubuntu release is not supported.

[B]The following packages have [COLOR=#ff0000]unmet dependencies[/COLOR].
 [COLOR=#ff0000]r-base : Depends: r-recommended (= 3.5.3-1trusty) but it is not going to be installed[/COLOR]
E: Unable to correct problems, you have held broken packages.[/B]

---

### Post by oktu on 2019-04-10
Thanks, but I fixed all by [COLOR=#990000][FONT=Arial]sudo apt-get install r-base-dev [/FONT][/COLOR][FONT=Arial]instead [/FONT][COLOR=#990000][FONT=Arial][/FONT][/COLOR][COLOR=#990000][FONT=Arial]sudo apt-get install r-base. [/FONT][/COLOR]&#8203;I don't know why....

---

### Post by huff2 on 2019-04-11
Read through the following link: [https://cran.r-project.org/bin/linux/ubuntu/README.html](https://cran.r-project.org/bin/linux/ubuntu/README.html)

This is an excerpt: 

> The other r-cran-* packages shipped with Ubuntu are installed into the directory /usr/lib/R/site-library.

 Installing R packages not provided with Ubuntu first requires tools  to compile the packages from source. These tools are installed via the R  development package with
 sudo apt-get install r-base-dev

---

