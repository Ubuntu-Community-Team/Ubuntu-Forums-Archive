---
title: "Unable to upload after fresh install"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by pkadeel on 2013-08-26
I can not upload a file or post anything, anywhere & by any method (i.e. browser or FTP) which exceed a couple hundred bytes. If I use live cd of 12.04 it works but not in 13.04

Please help

---

### Post by bkline on 2013-08-26
Just to be sure, you're saying you have successfully transferred very small files across the network?

---

### Post by pkadeel on 2013-08-26
yes small files and forms upto 368 bytes via browser and 1374 bytes via  filezilla. Can't even post a details here cause it will grow  beyond 368 bytes

---

### Post by bkline on 2013-08-26
What are the symptoms?  Error messages?  Is this a fresh install of Ubuntu 13.04?  Are you running 13.04 on the same hardware and network as was used for the 12.04 Live CD test?

---

### Post by pkadeel on 2013-08-26
same laptop & network. Live CD Ubuntu 12.04. Currently installed OpenSuse 12.3 but problem remains in Kubuntu 13.04, Fedora 19, Mint 15

---

### Post by pkadeel on 2013-08-26
Browser symptom: varing symptoms depending on which server is being used. This forum gives error about blank post
Filezilla: uploads a 0 byte file

---

### Post by bkline on 2013-08-26
Can you confirm that the Live CD Ubuntu 12.04 still works?  If you're experiencing the same failures on all of those distributions, it seems likely that the problem is unrelated to which version of the operating system you're running.

---

### Post by bkline on 2013-08-26
Can you provide details as to how you've determined that the transfers of the smaller files are successful?

---

### Post by pkadeel on 2013-08-26
yes I confirm that Live CD of 12.04 works cause I have just updated my website by live booting the laptop. This is what troubles me that all recent distros are causing this problem.

---

### Post by pkadeel on 2013-08-26
while I was testing distros, I had no file to upload so I created a  small text file which went through but when I uploaded a larger file it  failed. So I got the exact sizes by hit and trial.

---

### Post by pkadeel on 2013-08-26
I increased the file sizes byte by byte and browser stopped uploading after 368 bytes and filezilla stopped after 1374 bytes

---

### Post by bkline on 2013-08-26
Are there any limitations on what you're able to download?

---

### Post by pkadeel on 2013-08-26
Apparantly NO cause I downloaded 5 other distros during last couple of days after finding out the problem in Kubuntu. Came here only when I felt being a noob.

---

### Post by bkline on 2013-08-26
Which of the distros were you running when you performed the successful downloads?

---

### Post by pkadeel on 2013-08-26
Now I am using live CD of ubuntu 12.04 so can answer in detail. I did a fresh install of LinuxMint 15 Mate and found the problem then I downloaded the distros Fedora 19 KDE & Gnome, OpenSuse 12.3 KDE and when I was testing OpenSuse from its Live image, I found that I can upload files so I installed it but later on after installation, I found that I could only upload small files. So now I have OpenSuse 12.3 KDE installed on this laptop when I downloaded Kubuntu 13.04 During testing of Kubuntu I found that it also shows same behaviour.

Edit:
I also tried through VirtualBox with OpenSuse 12.3 as host and Win 7 as guest and using virtualbox NAT adapter thinking that it shall bypass Linux but IE 9 in win7 allowed me slightly higher bytes around 500 something.

---

### Post by bkline on 2013-08-26
> **pkadeel said:**
> Now I am using live CD of ubuntu 12.04 so can answer in detail.
That seems to imply that not only are you unable to post/transfer files, you are also unable to enter and post lengthy values for text form fields on web pages. Right?
> **pkadeel said:**
> I did a fresh install of LinuxMint 15 Mate and found the problem then I downloaded the distros Fedora 19 KDE & Gnome, OpenSuse 12.3 KDE and when I was testing OpenSuse from its Live image, I found that I can upload files so I installed it but later on after installation, I found that I could only upload small files. So now I have OpenSuse 12.3 KDE installed on this laptop when I downloaded Kubuntu 13.04 During testing of Kubuntu I found that it also shows same behaviour.
The pattern which is emerging appears to be that you can transfer any amount of data in either direction as long as you are running from a CD, and as soon as you try running from an OS which is actually installed on your own computer's disks uploads of any appreciable size fail.
> **pkadeel said:**
> Edit:
I also tried through VirtualBox with OpenSuse 12.3 as host and Win 7 as guest and using virtualbox NAT adapter thinking that it shall bypass Linux but IE 9 in win7 allowed me slightly higher bytes around 500 something.
Some of my original assumptions, which were based on the forum section in which you chose to post your original problem ("Absolute Beginners") are beginning to erode.

Did you answer the question asking for the details of how you determined that smaller files actually arrived at their destination intact?  Do you have tools (a shell account on the target machine, for example) which allow you to inspect the uploaded files?  Have you tried with more than one target machine (preferably on a different network than the one used by the original target)?  Is this a new laptop?  Has it ever been able to behave correctly with any earlier version of Linux actually installed?  With any version of any operating system installed?  What do you install on the machine after installing the OS?  Have you tested without adding any software not provided by default installtion?  We're trying to find out exactly what's different between the Live CD behavior and the "installed" behavior.  Are you doing any non-standard partitioning of the disks?  Do all of the filesystems have adequate space?  Can you provide the output from the df command in a console window?

---

### Post by pkadeel on 2013-08-26
> **bkline said:**
> That seems to imply that not only are you unable to post/transfer files, you are also unable to enter and post lengthy values for text form fields on web pages. Right?
Right

> **bkline said:**
> The pattern which is emerging appears to be that you can transfer any amount of data in either direction as long as you are running from a CD, and as soon as you try running from an OS which is actually installed on your own computer's disks uploads of any appreciable size fail.
Only Live CD which is infact a backup of my previous Ubuntu 12.04 install on this laptop under discussion. All other Live CDs of recent distros have failed to allow upload.

> **bkline said:**
> Some of my original assumptions, which were based on the forum section in which you chose to post your original problem ("Absolute Beginners") are beginning to erode.
I posted here because I am not well versed in Linux specially the console. Started using it in October last year. In other fields of computing I am not that absolute beginner.

> **bkline said:**
> Did you answer the question asking for the details of how you determined that smaller files actually arrived at their destination intact?  Do you have tools (a shell account on the target machine, for example) which allow you to inspect the uploaded files?  Have you tried with more than one target machine (preferably on a different network than the one used by the original target)?
Well i figured it out accidentally. Yes the file gets uploaded intact if it passes through otherwise if it is being uploaded via web page then it never reaches destination and if I use an FTP client then only a 0 byte file gets created on the server. Similarly I figured out that I can also not post lengthy forms when I tried to post here on this forum with details and could only send one liner posts. I have FTP access to only one target server but I tried through web pages on many servers.

  > **bkline said:**
> Is this a new laptop?  Has it ever been able to behave correctly with any earlier version of Linux actually installed?  With any version of any operating system installed?  What do you install on the machine after installing the OS?  Have you tested without adding any software not provided by default installtion?  We're trying to find out exactly what's different between the Live CD behavior and the "installed" behavior.  Are you doing any non-standard partitioning of the disks?  Do all of the filesystems have adequate space?  Can you provide the output from the df command in a console window?
It is not a new laptop almost 2 years old. I told you earlier that I was using Ubuntu 12.04 on this laptop. Before Ubuntu it was running Win 7. I don't know why I decided to install Mint 15 but it was a bad decission.

The difference is not between Live CD and installed OS cause if it had been then all other distros should have been successfull while tested in Live mode.
In my opinion the difference is between Old version and new version of softwares either the kernel or java which comes pre-installed in all the distros I have tested or may be the wifi driver (if it is changed in new distros)

Yes I have non standard partitions on a 500 gb disk and all the partitions are almost empty cause it is a fresh install and this partitioning scheme was working perfectly under Ubuntu 12.04
boot partition 250 mb
root partition 50 gb
home partition around 300 gb
another partition of around 100 gb which is mounted at /home/vboxvms
swap partition 4 gb

For the output of df command I will have to go back to the original installed OS and I will do it tomorrow.

---

### Post by bkline on 2013-08-26
I'm starting to feel as if I'm losing my grip on this thread.  I don't see any indication (before your most recent reply) that you had been using any version of 12.04 on this machine except the Live CD.  And the reports you provided of the outcomes for trying live mode (Ubuntu 12.04 and OpenSuse 12.3 KDE) were of successful uploading.  If you reported failures from any live mode tests I missed those messages.

Your theory about changes to the wireless drivers seem more promising than anything else that's surfaced so far (though for that to be the cause, the drivers supplied with the live CDs for both Ubuntu 12.04 and OpenSuse 12.3 would have to have been unbroken, only to be replaced by broken drivers by package updates, which while not impossible, doesn't seem too likely).  Easiest way to test this theory would be to hook up an ethernet cable to the machine.  If that doesn't help, I'm afraid I'm all out of suggestions.

Good luck.

---

### Post by pkadeel on 2013-08-27
Well the idea to checking via ethernet cable also came to my mind but I was not sure what the problem might be so may be due to laziness I didn't check that. Now when you also advised it, I checked it via ethernet and it works normally so now we can be sure that it is infact a Wifi driver problem. Thank you. I will now post the problem in the appropriate section.

---

