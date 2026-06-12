---
title: "Mythbuntu 9.10 - Can't find all channels, wrong time, can't connect to internet"
date: 2009-11-17
forum: Mythbuntu
---

### Post by Rocko262c on 2009-11-17
Mythbuntu 9.10 (Installation disk had no errors)
Hauppauge WinTv-HVR-1200
Front-end and Back-end installed.
Dell Dimensions
Brisbane, Australia

I installed Mythbuntu 9.10 on November 15, 2009.

1.0  The sound is faint.

2.0  Scanning doesn't pick up all channels here in Brisbane.  I have entered the proper transports and then scanned them and the channels are properly identified, but when you go to watch them I get a message that looks something like below:

signal 99%|S/N 2.4dB|BE 42|(LMs)Partial Lock

and the channel won't view and there is no information about the channel.  Why does windows take a long time to scan the channels and identifies all of them, but Mythbuntu is really quick and can only find one channel?

3.0  When I turn on MythTv with an automatic boot, it gives me a message "Could not connect to the master backend server -- is it running?  Is the IP address set for it in the setup program correct?".  How do I get rid of this

4.0  I tried to fix the firmware from [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200"), but this page is out of date.  I downloaded the drivers from the Hauppauge homepage and rm the *.rom files to *.fw files and tried to extract the firmware from the *.sys file but failed (mdsum error or something)?


Has anyone ever got their Hauppauge WinTv-HVR-1200 to work with any distro's of MythTv?

Thanks in advance,
Rocko

---

### Post by dibuntux on 2009-11-17
We just completed the DSO (Digital Switch Over) here in Rome & scanning with 0.22 is still a mess. I got partial lock on most networks, where VLC can lock and show all channels (even one new in HD at 1080i H264). 
I upgraded to 9.10 just for the "new" scanning features... not better than the old ones. 
This only on DVB-T, of course, sat channels work fine.

Sometimes (rarely) I get a "can't find mythbackend...", usually I give it an OK and it disappears.

As for the firmware, I had to 
sudo apt-get install linux-firmware-nonfree 
to get my HVR1110 work right.

I also found that increasing signal timeout gives better results, and also deselecting the box "free only channels" for recognising some MUX that contains FTA and cripted channels.

The big Partial Lock problem remains!

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 8400GS 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
HVR1110 DVB-t

---

### Post by Rocko262c on 2009-11-17
Thanks Dibutux,

I also noticed something funny when I scanned the channels.  While scanning, the Signal/Noice: status remained at 0% the whole time.  Did you have this problem before??

I found all the channels after increased the signal timeout as you had suggested.  The names were immediatley recognized after the scan, but when I went back to the front-end, some of the channels couldn't be viewed.  I got a message saying:

signal 99%|S/N 2.4dB|BE 42|(LMs)Partial Lock

as I did before in my origional post.  Any thoughts/suggestions?

What do you think about going to Mythbuntu 8.04 and installing the firmware manually as per ([http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200"))?

Thanks in advance,
Rocko

---

### Post by dibuntux on 2009-11-18
Dear Rocko,
the problem is exactly that one: the channels are found by the scan, but when you try to show them you get a partial lock; in my case now the signal strenght went from 60 something to 70 something % (increased with the recent DSO in my region), but still I get a BE of 65535. I do not think it is a problem with the firmware or the HVR-1110 at all, since using another program like VLC I can tune in any of those channels.

Again, the problem is mythtv tuning section for DVB-T.

Anyone has an idea?

---

### Post by Rocko262c on 2010-01-12
Dear Everyone,

I recently did a fresh install of Mythbuntu 9.10 with my Hauppauge WinTV-HVR-1200.  I did nothing to make the device work as it works with the new kernel just fine.

It seems that the issues come when scanning for channels.  Here are some configurations for Brisbane, Queensland, Australia and how to scan the channels properly.


1.0  Install Mythbuntu 9.10 frontend and backend and restart Computer, make sure that the infrared sensor is plugged in via usb before installing and that your remote has batteries. Most Hauppauge WinTV-HVR-1200 cards are sold with the remote and infrared sensor.  When you have the chance to configure a remote, select "Windows Media Center transceivers/Remotes(All)".

2.0  Exit from the frontend and then click on System->Administration->MythTV Backend Setup, click on "yes", enter password.

3.0 Here are some of the configuration settings that i changed in the Backend Setup
      General Setup - 
          TV Format:  PAL
          VBI Format:  PAL Teletext
          Channel Frequency Table:  Australia
          Local time zone:  None

      Capture Card Setup
          The device should show as:  /dev/devb/adapter0/frontend0
                                                 NXP TDA10048HN
                                                 DVB-T
           Signal timeout:  30,000
           Tuning Timeout: 40,000

4.0  Next, is the most important part, scanning the channels.  You can scan the channels in a couple places in the Backend Setup.  I choose to scan the channels under the &#8220;Channel Editor&#8221;.  Make sure that when you scan you choose &#8220;Full Scan (Tuned)&#8221;, and scan &#8220;ALL&#8221; so that you can get music stations if you want.  Enter the following information for each time you scan each frequency

226500000   7MHz  Auto  QAM-64 Auto Auto 8K  1/16  None
191625000   7MHz  Auto  QAM-64 Auto Auto 8K  1/16  None
177500000   7MHz  Auto  QAM-64 Auto Auto 8K  1/8  None
219500000   7MHz  Auto  QAM-64 Auto Auto 8K  1/16  None
585625000   7MHz  Auto  QAM-64 Auto Auto 8K  1/8    None

Remember, this is for Brisbane, Queensland, Australia.  Check with your local area for the proper station information.


TIME CONFIGURATION
I could not edit this and tried several time as I choose the option to manually set the time, it was just not possible to edit manually.  I just made sure that in the Backend Setup, General Setup that the Local time zone was set to "None" and exited this setup.  Then I connected to the internet and the operating system connected to some time server and updated the time automatically.....I am not 100% sure this is the case, but this is how i fixed the time problem.

I think someone might have trouble if they are installing in an area that has no internet and this issue should be resolved with the Mythbuntu developers.....I have no idea how to raise this issue with them.

Internet Connection 
I am using a USB dongle and it just didn't want to work in the last install....this is totally separate issue.  It did however work in this install after playing the installing and rebooting game several times.

Hope it helps,
Rocko262C

---

### Post by dibuntux on 2010-01-13
Re: 9.10: DVB-T No Lock on almost all channels
Ok, after a LOT of trying, I solved this.

------------------------------------------------------------
MYTH DEVELOPERS take note: DVB-T scan is broken
------------------------------------------------------------

As I said, I've a splitter on my antenna cable, and I connected a cheap STB DVB-T to a standard TV set. On this particular model (mp@man) if you double press INFO button, you get ALL the info related to the Multiplex you are watching:
Freq Ch FFT Mod Gi Feq PID Signal% - so for example:
754Mhz 56 8K 64QAM 1/4 5/6 620 77%

From another table or wscan (which is unable to get all those parameters), I also got the Band, 8 MHz in the above case.

I erased all channels. I Inputed MANUALLY those parameters in the Transport settings on Myth and did a rescan for the transport.
I got the same channels as before, BUT NOW THEY ALL GET A LOCK!
Modified all others Transport with the info from the cheap STB receiver and rescan - now everything works.

So the moral of the story is: Myth cannot reliably scan a transport using Auto as a parameter for the above sections - You need to have those from somewhere else, or the scanned channels will not get a lock (or partial lock).

This was probably the most annoying problem I found on Myth - and the most undocumented one.

It is sad that a cheap STB can scan correctly and Myth cannot - but hey, what-the-heck, besides this Myth ROCKS!

Hope this helps others with DVB-T
dibuntux is online now Report Post   	Edit/Delete Message

---

### Post by Rocko262c on 2010-01-13
Hey dibuntux,

I am sure that you were 100% successful in manually editing the transports and rescanning to find all the channels, I don't dispute this, but unfortuantley I tried that method and it didn't work for me and my Hauppauge WinTV-HVR-1200.

The key parameters that I changed that had the biggest effect were changing the Signal timeout to 30000ms, the tuning Timeout to 40000ms, and scanned each frequency by &#8220;Full Scan (Tuned)&#8221; while entering the channel info according to my last post.

Thanks for contributing,
-Rocko

PS I agree MythTV does Rock!

---

### Post by dibuntux on 2010-01-13
Mmmh... your timing value are 10 times higher than default; never tried a full scan using those...

Anyway, I arrived to the method of inputting directly all those parameters after reading an article about DVB-T standard, or better the lack of it. Infact, it appears that the problems relies in the NIT preamble that is suppose to inform the receiver about local parameters on the specific MUX. 
It just seems that Myth is not capable of getting a lock using Auto, when it can using manual parameters.
Of course the limit of this method is that you need a DVB-T STB capable of showing that infos.

Glad that it works for you anyway. I just got a Nova T-500 dual DVB-T. Will try that & let you know.

---

