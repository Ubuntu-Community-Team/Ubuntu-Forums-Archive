---
title: "Hauppauge HVR 1100 - No channels!"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Spermy on 2007-03-27
I am New to linux user on Ubuntu dapper, have a hauppauge HVR1100 tv card and am having trouble getting it to find channels.... I can view and hear the composite input perfectly fine, but cannot find any scanned channels.


I have looked for guides and how-to's but being a linux N00BIE I don't understand half of the commands or dialect. I do not believe that I have the "scan" program or the "tzap" program installed, I am currently using tvtime.

I would like to maybe use mythTV in the future when not so new to linux, but for now I'll settle with getting tv to work.

Any help would be appreciated. Thanks in advance, 

                 Nick

---

### Post by Spermy on 2007-04-01
Bump.


However, I have reinstalled my PC completely, Xp on the first 30Gb, followed by 20Gb for Ubuntu 6.06 LTS a 60 Gb /USR and 2Gb Swap. Leaving my other 200Gb drive as an ext3 partition. (I found a windows program called IFS something or other to let XP acces it as a shared drive.

Still I digress, I can STILL only see My xbox through it as a composite input, complete with sound!!!
WOW go me.
However, I still cannot find any channel at all. 

Am in the UK, using TVTIME, I've followed several guides, howto's and followups saying that 'I tried this...' and I can't get anything.


Please help.

---

### Post by Spermy on 2007-04-02
Gee, So many helpful people!



What do I have to do To get some help, even if it's help from another 'noob' or clueless person...

---

### Post by Jovec on 2007-04-02
> **Spermy said:**
> I am currently using tvtime.

TVTime only works with frame grabber cards, not mpeg encoders.

Try this for me, **either**:

Start the VLC player (not installed by default), and File -> Open Capture Device, click on the PVR tab, leave the options defaulted, and click OK.  Anything?

Or from a terminal:

cat /dev/video0 >> test.mpg

Let it run for a 5-10 secs, then CTRL+C to cancel.  Then, open the file test.mpg with any standard movie application.  Anything?


FYI, I watch TV using VLC like I described above, running the command "ivtv-tune -d/dev/video0 -cXX" from a terminal to change channels.  Not pretty, but it works for me.

---

### Post by Spermy on 2007-04-02
What was the point of leaving the options defaulted and clicking OK.... Should it have done something?




K. I now have a 98 Mb file called test.mpg that Totem won't play. Will boot to windows to check it.....
Hmmmmmmmmm.


and it says command not found when i try the "ivtv-tune -d/dev/video0 -cXX" (i used 10 instead of xx... was guessing it was a channel!

---

### Post by Spermy on 2007-04-02
K. Haven't got anything that will play it.... And my codec informing software (To tell me what codecs it needs) Says unsupported.

So I got 100Mb of nuffin. Bummer!

Am greatly appreciating the help though.

---

### Post by Jovec on 2007-04-02
> **Spermy said:**
> K. Haven't got anything that will play it.... And my codec informing software (To tell me what codecs it needs) Says unsupported.

So I got 100Mb of nuffin. Bummer!

Am greatly appreciating the help though.

I want to check that your card is supported at ivtvdriver.org, but the site seems to be down atm.  In the meantime, you can try reading this link for some helpful info:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)  and
[https://help.ubuntu.com/community/Install_IVTV_Troubleshooting](https://help.ubuntu.com/community/Install_IVTV_Troubleshooting)

Also, just to be sure, you did use /dev/video0 and not /dev/video when you ran "cat /dev/video0 >> test.mpg" ?

---

### Post by Jovec on 2007-04-02
OK, new thing.  Doing my best, but I am not familiar with the HVR-1100.  I use a PVR-150.

Repeat the VLC test for me, but instead use the Video4Linux tab.

It appears the the HVR-1100 is supported through the video4linux drivers, and not through the ivtv ones.  There also appears to be two HVR-1100 cards using different encode chips.  See [http://en.wikipedia.org/wiki/Hauppauge_Computer_Works#Table_of_products](http://en.wikipedia.org/wiki/Hauppauge_Computer_Works#Table_of_products)

It would probably be helpful to identify which you have.  Post the output of " less /var/log/dmesg | grep Hauppauge"

---

### Post by Spermy on 2007-04-03
Cheers again, but using the Video 4 Linux tab didn't appear to do anything either.

Typing "less /var/log/dmesg | grep Hauppauge"
Gives
> [17179588.176000] CORE cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]
[17179588.332000] tveeprom 2-0050: Hauppauge model 94009, rev C2A0, serial# 321674
[17179588.332000] input: cx88 IR (Hauppauge WinTV-HVR110 as /class/input/input3
[17179588.468000] CORE cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]


And just incase you wonder......
The output of "lspci -v" (Or at least the corresponding results for My tv card....)
Gives
> 0000:01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 9402
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at da000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

0000:01:08.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 9402
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at db000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

0000:01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 9402
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

0000:01:08.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 9402
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2



Am getting mighty lost now....If only it were noticably easier..!!!!!!!

The rest of linux has been a comparative doddle...........Inc. The ATI drivers!

---

### Post by Jovec on 2007-04-04
Output of ls -l /dev/dvb ?

I'd suggest rading here:
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

---

### Post by Spermy on 2007-04-06
Output of ls -l /dev/dvb 
Gives

> total 0
drwxr-xr-x 2 root root 120 2007-04-06 12:37 adapter0


And using that linuxtv wiki page, I managed to find and create a channels.conf, However I still cannot tune to a broadcasted channel, using either tvtime or vmplayer. I even tried gxine as a following example suggested and still no avail. 

No, scratch that.. Gxine does work even get audio..... Just still don't get anything using vmplayer or tvtime...

So suppose problem solved.!!!

Edit::::::::::
Thanks for all the help.....I'll see if I like using Gxine and hopefully I'll get along with it...

---

### Post by captain.kipper on 2007-04-21
You are the only person I have found to get the 1100 working in linux. Well done! Could you please give me a few tips?

For me tvtime is the only program to give anything, but it only shows analogue tv video, with no sound. VLC nothing. Gxine gives error : no stream found. How did you get it to work?

Cheers

---

### Post by Spermy on 2007-04-22
Well, it was a long hard struggle, until the post before I'd gotten it sorted...............


Unfortunately I have installed some software updates since it was working ( And I gaurantee it WAS working!) and now Gxine has decided "no input plugin found"......
so as soon as I get some time to look at it again (Damn private life gets in the way!) hopefully this evening, I'll have a look into sorting it out again!

I never quite got round to scanning for terrestrial broadcasts with it, as the digital ones were found, so I saw no point.... Don't therefore know if that part worked. also I never tried the composite input with Gxine..... So again, can't say if that worked either!

Sounds absolutely awful, but I will have a look soon and get back to you....

Hopefully even as a "n00b" or wot-not, i'll be able to help...

Although getting Gxine to show any channels was problematic, I eventually used the aforementioned post to get a channel list, and then through switching user to sudo (Actually had to log in as him!) i managed to place the channels list file in the right place to get it working....

---

### Post by stfu on 2007-04-23
Mine works only after reboot for a while when i modprobe cx88-dvb. it creates device in /dev/dvb/adapter0, it just stops working after I watch it with kaffeine and exit. Haven't really tried that hard though.

---

### Post by cblanquer on 2007-05-05
In my case I could make the HVR 1300 work after recompiling the video drivers t getting DVB part enabled.
Results are :
[LIST]
[*]Kaffeine works fine for DVB-T channels
[*]my Logitech Quickcam webcam does not work anymore
[/LIST]

It seems there is a conflict on the handling of video drivers as recompiling webcam ones drove me to lose again TV card access.
I am posting this in case anybody would be under the same trouble.
To be continued...

---

