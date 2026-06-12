---
title: "Installing latest NVIDIA 270.41.06 on Ubuntu 10.10 64bit for GTX 580"
date: 2011-04-21
forum: Multimedia Software
---

### Post by amurthy on 2011-04-21
Yesterday, NVIDIA released a new set of drivers. For ubuntu 10.10, I downloaded 270.41.06. I havent been able to set it up on my fresh install of Ubuntu 10.10. 

I have tried the following methods:

1. First changed the settings for updates to accept proposed updates. This is also suggested at [http://joeslifewithubuntu.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html](http://joeslifewithubuntu.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html)

Then installed the additional driver proposed by Ubuntu.

On restart, no login-screen. (Xserver fails to come up!)

2.Edited the repos by adding ppa:ubuntu-x-swat/x-updates. Unfortunately 270.41.06 is not the latest driver available there - 270.41.03 is the current version. On adding this repo the driver is searched successfully by synaptic. Installing nvidia-current brings up the driver version to 270.41.03 without any issues.

Nvidia X Server Setting prompts to run the nvidia-xconfig. On doing so a new conf file is created.

On restart, the Ubuntu splash screen is not displayed. Again Xserver fails to start!

3. Finally, I tried installing the .run file provided on Nvidia's website. First, I dropped to a root shell. Then cd'ed to the location where .run file was saved. On running the .run file, the installer asks you to change the run-level to 3. On doing so by telinit 3, the driver starts installing. As soon as I accepted the terms and proceeded to the next screen, a warning was displayed saying the pre-install script had failed!

But the driver installation does proceed to completion. 

Alas! even this method failed. The Xserver still does not start. No splash screen.

Currently I am running the system by restarting the Xserver in failsafex mode.

Please help.

---

### Post by coolcaseley67 on 2011-04-23
Hello ,

I happen to be the Joe behind the blog . Please note the post is for version 96 ONLY ! . I do know not about  know any other drivers !  

By change are you the Guy who commented about 64 bit Ubuntu ?

Have you read the Readme for the driver here : [http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/index.html")

---

