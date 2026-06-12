---
title: "No wireless, Dell Vostro 1320, overwritten Windows!!!"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by bat717 on 2010-10-11
I'm so stupid.
I am a COMPLETE beginner when it comes to Ubuntu, and linux in general. I've been wanting to try it for a while, and today I bought a magazine, Linux User and Developer, that had a disc with it that included Ubuntu 10.10. It said you could install it from the disc. So I inserted the disc, restarted the computer and booted from it. I thought I followed all the instructions correctly to install it alongside my Windows Vista partition, but obviously not, as my entire partition was deleted with all my files. Oops. Please don't laugh!
So moving on from that, I decided I would just use Ubuntu. But I can't get the wireless network to enable. I'm online using a mobile dongle, but it's very slow, and I'd like to use the WiFi. It's not my house, so I can't connect to the router, and I wouldn't have a clue what I was doing. To be honest, I don't have a clue what I'm doing anyway! I've installed the Broadcom STA, and it says it is activated and currently being used. But the option to connect to a wireless network is greyed out and it says wireless is disabled. I don't know how to enable it! Wireless was definitely turned on in Windows before I deleted it. It's controlled by a hardware switch on the side of my computer.
Please, please help! I am such a beginner at this, and the Terminal scares me, so please explain everything to me fully if possible!
Thank you so much.

---

### Post by bat717 on 2010-10-13
Please help me!

---

### Post by bobbob1016 on 2010-10-13
Try System -> Administration -> Hardware Drivers
You might be able to install the drivers from there.  Further than that, I don't know since everything I'm seeing on google says wifi should just work.

---

### Post by johnnytm on 2010-10-13
there are a couple of links posted in this thread which may be of some help to you. [http://ubuntuforums.org/showthread.php?t=1594577](http://ubuntuforums.org/showthread.php?t=1594577) This is also a dell vostro but its a 1520 instead of 1320. It may be worth a shot. Especially if you have a BCM4312 wireless adapter.

---

### Post by bat717 on 2010-10-14
I tried everything on those threads, thank you, but nothing helped. The wireless indicator isn't on, although I have the hard switch switched to on. The light doesn't come on when it's on off either! I have the drivers installed, but just can't enable the wireless. This is driving me insane! I'm SURE it was turned on when I... Ahem... Overwrote Windows!
Any other ideas anyone? Please?
Thank you!

---

### Post by johnnytm on 2010-10-14
this may be kind of a stupid question, but when u click on the network manager and it says wireless disabled, did you try clicking on that. if you move away from the network manager after doing that and then going back to it, it might then show wireless enabled. It doesnt change in the window as you click it. but other than that there is a link from braodcom that has some other ideas [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by bat717 on 2010-10-15
Tried clicking the wireless disabled in network manager (that is the menu that comes when you click/right click on the wireless indicator yes?) and nothing happened even when I went back to it. From the read me, I understood very little, but the driver I installed was that one and it does say activated and currently in use. I read somewhere that you need to change something in windows to allow the wireless to stay on, which I'm sure I've done in the past when I have installed ubuntu using wubi, but obviously I can't go back to check, as I have no windows! Is there any way to make the hardware switch to turn wireless on work in ubuntu? I have a feeling that that is the problem. 
Thank you.

---

### Post by TBABill on 2010-10-15
I am not certain this is similar to your problem, but you can review it and take steps contained to see if it helps. This worked for others with the Broadcom BCM4312.
 
[http://ww.ubuntuforums.org/showthread.php?t=1593112](http://ww.ubuntuforums.org/showthread.php?t=1593112)

---

### Post by bat717 on 2010-10-15
Thank you so much! All is now fixed! You are a genius!

---

