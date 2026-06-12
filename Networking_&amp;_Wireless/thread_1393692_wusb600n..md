---
title: "wusb600n."
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by GazRockK on 2010-01-29
> Originally Posted by **mizunoX**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6112069#post6112069")                 
                 [I]I've noticed a few posts from people frustrated with the WUSB600N and the lack of support for it in Ubuntu/Linux so I thought I'd set the record straight for those searching the forums for answers.

The Linksys WUSB600N doesn't work in Ubuntu out of the box (current as of the release of Ibex)
Also it does not play nice with ndiswrapper (frequent disconnects, no 5Ghz support, no WPA2 support)

I was able to get it working with 5ghz and WPA2 by following steps that I found here:
[https://answers.launchpad.net/ubuntu/+question/45440]("http://posting%20on%20external%20website/")
Credit goes to the original author.

I've downloaded and modified the driver source for your convenience.  

Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar](http://rapidshare.com/files/160951015/WUSB600N.tar)
Step 2 - Extract WUSB600N.tar to a folder
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder
Step 4 - type "sudo make" without quotes
Step 5 - Copy the file:
[LIST]
[*]sudo mkdir /etc/Wireless
[*]sudo mkdir /etc/Wireless/RT2870STA
[*]sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
[/LIST]
Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.

The wireless card should now be working.[/I][I]

So far, I'm stuck on step one. Why? Well It's Rapidshare. 
I've constantly been trying to download that one file, but apparently I need to "check back in two minutes as all of their free uploading spots are taken." And of course, they never cease to mention that the wait can be gone at 7Euros a month. Could anyone give me another driver download link? If they can't, for those of you who DO have the file, could you upload it on mediafire etc or send it to my spam account if possible (sst__tank900@hotmail.com) Thanks.
[/I]

---

### Post by pdc on 2010-01-29
strange; worked for me first time; 

reluctant to contact to unknown email addresses; 

is this alternate source any good?

[http://yorapidshare.com/rapidshare/wusb600n%20tar.html](http://yorapidshare.com/rapidshare/wusb600n%20tar.html)

---

### Post by GazRockK on 2010-01-29
Sorry, no good. I tried downloading the file again but still got the same thing. If really don't want to give your email away, make a spam account of your own and send it through there. I really want this file. Thanks.

---

### Post by GazRockK on 2010-01-29
Nvm. Someone sent me the file. thx to whoever did.

---

### Post by pdc on 2010-01-29
the idea of a "spam account" is new to me:

could you enlighten us on how you do this?

---

### Post by wimux on 2010-02-02
Thanx for the tip, but I cannot finf the file "[I]rt2870sta.ko" in the linux-folder.

What am I doing wrong?

[/I]

---

### Post by chili555 on 2010-02-02
Did all the steps, especially step 4, proceed without any errors? Retrace your steps, starting at step 3, add a new step 3a:```
sudo make clean
``` and tell us what happens at step 4. Thanks.

---

