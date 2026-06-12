---
title: "9746 nvidia driver just not working after new kernel in dapper"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by PartisanEntity on 2007-02-10
As you may be aware, there was a kernel update recently and many users who had 3rd party nvidia drivers were forced to reinstall the nvidia drivers. In many cases this doesnt seem to have been too much of a problem, however some people have had isues:

I am using **Dapper**, I have an nvidia GeForce Go 6200 card in my laptop. Initially I was using the nvidia-glx drivers from the repos. I then used this method to update the drivers to the latest version (9746):

[http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html)

I added tseliots repo and did a:

```
sudo aptitude update && sudo aptitude dist-upgrade
```

This updates my graphics card drivers to 9746.

Then came the kernel update, after rebooting X server could not load. So I did:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

The installer checked the for newer drivers, didnt find any and then compiled the drivers. during the installation it mentioned having to guess the location of the modules and advised that should X server still crash i should install pkg-config and X.Org SDK/development package.

Finally the installer was done and X server again could not load and gave an API mismatch error.

(I tried envy with the same outcome).

I just cant seem to get the 9746 drivers to work the with latest kernel update in dapper and i am not experienced enough to know where to look for the problem.

I thought this might have to do with the pkg-config and X.Org SDK/development packages that were mentioned in the error. I checked the repos, pkg-config is installed. The other package is not installed and I cant install it because some dependencies wont be installed (i dont know why).

I even re-tried the method I had used back then to update the nvidia drivers through tseliots site but since the kernel update it wont work.

So if there is anyone out there who is experienced I would really appreciate some help.

Thanks.

---

### Post by PartisanEntity on 2007-02-11
I have tried it quite a few times, and basically after the kernel update, if I try to install the 9746 drivers I get 'API mismatch' and 'cannot find modules' errors.

Can anyone shed some light on this?

---

