---
title: "Help No Sound in 10.10, Sound works fine in Windows 7 Boot"
date: 2010-11-25
forum: Multimedia Software
---

### Post by xcalx29 on 2010-11-25
To start off, i am about 3 days into my new ubuntu operating system.  I am a complete newbie, but i have picked up alot in the last couple days.  My sound was previously working, but the microphone was glitching when using skype.  After running a bunch of different commands in terminal that were posted on forums from all over the internet, i rebooted my computer to find no sound.  I have searched the forums again and tried many different command lines in terminal to no avail.

My system setup is found here:
[http://www.alsa-project.org/db/?f=3d61093b76bda95fd2b8821ec466621db5e62ed9](http://www.alsa-project.org/db/?f=3d61093b76bda95fd2b8821ec466621db5e62ed9) 

Can one please help me???

---

### Post by xcalx29 on 2010-11-26
Any Help???

---

### Post by lidex on 2010-11-27
Your alsa install is borked, try re-installing.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Afterward get updated alsa info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by johnmay on 2010-11-27
Lidex,

Here are two sound profiles for my 10.10 system which has no sound.. 

The first with a USB sound card which works provided that I use only headphones in the front usb port. With the back ports, something shorts out the sounds.

[http://www.alsa-project.org/db/?f=abc1927807f8142dfa54eb1770d69af0f321c3dc](http://www.alsa-project.org/db/?f=abc1927807f8142dfa54eb1770d69af0f321c3dc)

Also, a PCI sound card which alsa can see, but has not worked at all in the 10.10 version. Also, it did not work in 10.4 now that I am talking about it. I have read somewhere that the chip set in the card is not the greatest. Here is its' profile: 

[http://www.alsa-project.org/db/?f=8a5aa5fa7f44f826088601fe42e95e116786bbbe](http://www.alsa-project.org/db/?f=8a5aa5fa7f44f826088601fe42e95e116786bbbe)

Any suggestions would be welcome. As of right now, my best solution is to remote to the system and chose local sound from the client.

Thanks

---

### Post by xcalx29 on 2010-11-27
I fixed it.  Thanks for all the help. had to delete the files from the system then reinstall

---

### Post by Bluebellmaniac on 2010-12-03
Hi, I am also having audio problems with 10.10. Absolutely no sound. Here is the Alsa link:

[http://www.alsa-project.org/db/?f=b49dd582f52ed43194232f9a7b1d9f7a51bb0864]("http://www.alsa-project.org/db/?f=b49dd582f52ed43194232f9a7b1d9f7a51bb0864")

I did the instructions from earlier in this post, but no change. 

Any help would be greatly appreciated!!!!

---

### Post by lidex on 2010-12-03
> **Bluebellmaniac said:**
> Hi, I am also having audio problems with 10.10. Absolutely no sound. Here is the Alsa link:

[http://www.alsa-project.org/db/?f=b49dd582f52ed43194232f9a7b1d9f7a51bb0864]("http://www.alsa-project.org/db/?f=b49dd582f52ed43194232f9a7b1d9f7a51bb0864")

I did the instructions from earlier in this post, but no change. 

Any help would be greatly appreciated!!!!

Ah, there is a bug. Go here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647)

---

### Post by Bluebellmaniac on 2010-12-04
Thanks lidex! 

I actually found that website / bug tracker today myself too! I wonder why the forum didn't notify me of your reply by email?

But I appreciate the help! The forum rocks!!!

---

