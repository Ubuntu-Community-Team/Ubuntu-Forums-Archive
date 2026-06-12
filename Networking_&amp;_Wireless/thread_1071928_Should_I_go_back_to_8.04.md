---
title: "Should I go back to 8.04?"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by sailthesea on 2009-02-16
Hi 
I have a longish question that only requires a short answer
 I benched 8.04 on this oldish Dell C640 and it looked great But decided to try a dual boot from win 2000 with Wubi and 8.10 its worked ok but the wireless issues are a pain, I just want it to work well. This thing should run xp no problem 
 Should I just go back to Hardy and wait for the wireless problems to be solved and see if Ibex works better?
 I'd love to try and help fix this but wireless networking is a bit like witchcraft to me When I was young computers had wood in them!
 Cheers

---

### Post by cariboo on 2009-02-17
8.10 has newer drivers than 8.04, it would help if you gave us a listing of your hardware. Open an Applications-->Accesories-->Terminal and type:

```
lspci
```

This will print out a listing of your hardware, whiich in turn will help us help you with your wireless problem.

Jim

---

### Post by sailthesea on 2009-02-17
Thanks cariboo 907
  I'll post that info when I can boot up with a working connection (in win at present)
 To be going on with I know it seems to be a common problem and I have searched for a solution, but I think some specifics are needed
 Thanks

---

### Post by sailthesea on 2009-02-17
Ok
 Used lspci in Terminal I got this out:

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
administrator@ubuntu:~$ 

  This seems to refer to all the internal systems My wireless connection Netgear  to the USB doesn't seem to show up. Booting into 8.10 detects my network, it connects but after a while slows down, stops, sometimes comes back and is generally not doing it
 Maybe this will let you help me with my problem
  Many Thanks
 PS Will regular updating help with this?

---

### Post by spcwingo on 2009-02-17
> **sailthesea said:**
> 
  This seems to refer to all the internal systems My wireless connection Netgear  to the USB doesn't seem to show up. Booting into 8.10 detects my network, it connects but after a while slows down, stops, sometimes comes back and is generally not doing it
 Maybe this will let you help me with my problem
  Many Thanks
 PS Will regular updating help with this?

Since it's a USB adapter post the output of:

```
lsusb
```

---

### Post by sailthesea on 2009-02-18
OK did that, output was:


administrator@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
administrator@ubuntu:~$ 


at least I know the hardware is recognized 

I'm on a bit of a steep learning curve with Terminal commands ie I don't know any of them! Is there a summary of the basic command structure I can look at?
 Thanks

---

### Post by spcwingo on 2009-02-18
Have you tried ndiswrapper?  If not, you can install it by do entering this command:

```
sudo apt-get install ndisgtk
```

This will install the GUI version of ndiswrapper.

Now you need the windows driver.  Check on your CD for files named wg111v3.inf and wg111v3.sys.  These are the driver files.  Now open ndisgtk (system>admin>win wireless drivers) and select new driver.  Now navigate to the CD and select the inf file.  Select OK and if your wireless card is recognized, you're golden.

---

### Post by sailthesea on 2009-02-18
OK Tried that but no dice finding any .inf files on the CD other than autorun.inf which doesn't open. The drivers have to be on this disc because I installed it on windows not long ago, I'm stumped! 
  Sorry I didn't come back sooner by the way I had to go on a job and this is geting soo o o  s   l   ow    
  Any ideas folks?
 Thanks

---

### Post by spcwingo on 2009-02-18
Okay, I downloaded the driver installer from Netgear and extracted the driver files.  I have uploaded them here:

[http://www.mediafire.com/file/nvjmt21zrtz/wg111v3_driver.zip]("http://www.mediafire.com/file/nvjmt21zrtz/wg111v3_driver.zip")

That will contain the required inf and sys file.  Please note that they are compressed, so they will have to be unzipped first.

Try using ndisgtk with those and let us know if it works or not.

---

### Post by sailthesea on 2009-02-18
THanks !!
 I will try and do as you suggest but am having real problems staying online long enough to do anything! One thing though' what should I use to unzip these files? 
 Stellar help by the way Cheers!!

---

### Post by spcwingo on 2009-02-18
If on your Ubuntu box you should just be able to right click and select "extract here".

---

### Post by sailthesea on 2009-02-18
I've been battling for days trying to get my Netgear usb wireless to work at anything better than nothing in 8.10 I've had some stellar help from you guys and I think I'm nearly there If I download and burn to cd the Windows .inf .sys files from the Netgear site that should enable me to use ndswrapper etc to properly install it from Terminal when I reboot Ubuntu shouln't it? 
Thanks

---

### Post by sailthesea on 2009-02-18
Wouldn't play 
I just kept getting redirected to gambling sites
Thanks for your help

---

### Post by thinking2loud on 2009-02-18
What have you done (or deliberately not done) in order to get it to work?

---

### Post by spcwingo on 2009-02-18
I don't understand why it's doing that.  Try this link instead:

[http://www.mediafire.com/?nvjmt21zrtz]("http://www.mediafire.com/?nvjmt21zrtz")

Hopefully this one will work.  If not, let me know and I'll see if I can upload it somewhere else.

---

### Post by sailthesea on 2009-02-18
Well not much
 Ive had a lot of people try to help me but it seems to come down to an issue of finding and downloading the right driver which I think I can do but noone really can confirm this If I put the wrong driver into Ubuntu it will fry my connection so I'm just being cautious 
 I need to come back to this coz I've got an early start 
 Feel free to leave me any tips for when I get in
Cheers

---

### Post by dmizer on 2009-02-18
Please do not create multiple threads for the same problem.

Please try this solution: [http://ubuntuforums.org/showpost.php?p=6759228&postcount=68](http://ubuntuforums.org/showpost.php?p=6759228&postcount=68)

---

### Post by sailthesea on 2009-02-18
Yeah 
 Sorry I am getting really frustrated with this !

---

### Post by sailthesea on 2009-02-19
Thanks for the link dmizer
That looks as if it will work I will try it later
Sorry for tying up the forum I've been swapping in and  out of platforms and lost track of my posts 
Thanks again everyone

---

### Post by dmizer on 2009-02-19
Just a word of advice, if you're getting really frustrated with something (especially computers), it's a really good idea to step away for a while and give yourself some time to both think and decompress.

You can find all of your previous posts by clicking on the search link in the tool bar. At the bottom, are "Find all your threads" and "Find all your posts".

Let us know if you make any progress, or if you have trouble! :)

---

### Post by sailthesea on 2009-02-19
Wise words Thanks you were right
I am trying the fix from your post and it seems to be going smoothly 
I will let you know my progress I'm very new to Ubuntu and the forums Thank you all for your patience

---

### Post by sailthesea on 2009-02-19
Amazing!
It's off like a scalded whippet!!
I'd never have figured this one out my own, it just goes to how important the forums are and how I should use them properly. So more than one lesson learned today!
Am off to explore the world of Ubuntu properly now. I'm sure I'll have plenty more questions though. Throwing away the windows mindset is not as easy as it sounds, if you get stuck you end up thinking about it the wrong way
Thankyou Wise People

---

### Post by dmizer on 2009-02-19
Glad to see we got you going! Enjoy!

---

