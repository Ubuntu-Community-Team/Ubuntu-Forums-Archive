---
title: "How to test tv tuners, watch tv"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Tdonohue on 2007-02-25
I have two tuners an analog kworld tuner, and the atsc-110 kworld tuner.  Both appear to be the  ones that use the saa713x.  I don't know if they're detected by ubuntu correctly.  I am in the process of installing mythtv, but I'm having problems, so I'd like to rule out the tuner cards.  I installed tvtime, but I don't know what to do next.  I open it up,  there's no TV, no options to select anything, no menu bar, and the documentation seems sparse to me.  

I can't find anything in the forum to help me, so apparently it must be something everyone can figure out but me.

One post I did find said to do   

cat /dev/video1 > ~/test.mpg  

and then watch it Mplayer.  Watch what and how?  

If I could just watch a signal through each input (2 analog, one digital) then I would know that they work correctly and I could proceed with my mythtv install.

Please help! Thanks.

---

### Post by Erlander on 2007-02-26
I installed Kaffiene for testing my card.

Works well.

Rob

---

### Post by Tdonohue on 2007-02-26
Thanks Rob, but I think my failed attempts at using tvtime mean I have a problem with my cards.

lspci -v shows:

04:08.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Philips Semiconductors [COLOR="Blue"]Unknown device [/COLOR]0000
        Flags: bus master, medium devsel, latency 32, IRQ 50
        Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

04:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
        Subsystem: KWorld Computer Co. Ltd. [COLOR="Blue"]Unknown device[/COLOR] 7350
        Flags: bus master, medium devsel, latency 32, IRQ 58
        Memory at fdbfd000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

It shows two multimedia controllers, and I have two pci tv tuner cards, but shouldn't it show three (one for the single analog tuner card and two for the dual atsc-110).  I very well could be wrong there though.

I'll look through the forums for a solution, if anyone has any ideas, let me know!

Thank you!

---

### Post by NT4usB on 2007-02-26
> **Tdonohue said:**
> I have two tuners an analog kworld tuner, and the atsc-110 kworld tuner.  Both appear to be the  ones that use the saa713x.  I don't know if they're detected by ubuntu correctly.  I am in the process of installing mythtv, but I'm having problems, so I'd like to rule out the tuner cards.  I installed tvtime, but I don't know what to do next.  I open it up,  there's no TV, no options to select anything, no menu bar, and the documentation seems sparse to me.  

I can't find anything in the forum to help me, so apparently it must be something everyone can figure out but me.

One post I did find said to do   

cat /dev/video1 > ~/test.mpg  

and then watch it Mplayer.  Watch what and how?...

mplayer -vo xv ~/test.mpg
-or-
mplayer -vo xv /home/{yourusername}/test.mpg
Not sure which is correct as I use: cat /dev/video1 > /tmp/test.mpg* to test mine.

*from [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

---

### Post by Tdonohue on 2007-02-27
> **NT4usB said:**
> mplayer -vo xv ~/test.mpg
-or-
mplayer -vo xv /home/{yourusername}/test.mpg
Not sure which is correct as I use: cat /dev/video1 > /tmp/test.mpg* to test mine.

*from [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Every one of those returned "Invalid argument".   Thanks though.  I briefly had one tuner working yesterday and the quality was so appalling, I  decided to use MCE2005 for tv.  This is the same tuner that looked great in my old MCE.  I'll dualboot and work on it when I have time because I think Mythtv will be great when the tv picture quality gets better.

---

### Post by lwtbenben on 2007-05-20
> **Tdonohue said:**
> Thanks Rob, but I think my failed attempts at using tvtime mean I have a problem with my cards.

lspci -v shows:

04:08.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Philips Semiconductors [COLOR="Blue"]Unknown device [/COLOR]0000
        Flags: bus master, medium devsel, latency 32, IRQ 50
        Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

04:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
        Subsystem: KWorld Computer Co. Ltd. [COLOR="Blue"]Unknown device[/COLOR] 7350
        Flags: bus master, medium devsel, latency 32, IRQ 58
        Memory at fdbfd000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

It shows two multimedia controllers, and I have two pci tv tuner cards, but shouldn't it show three (one for the single analog tuner card and two for the dual atsc-110).  I very well could be wrong there though.

I'll look through the forums for a solution, if anyone has any ideas, let me know!

Thank you!

Yeah, I have the same infomation as you in my Ubuntu.
So, is this right and I still can not see any tv using tv player just like xawtv or xine
Could someone guide me out of this nightmare?

---

### Post by nekit on 2007-05-20
OOOOOOOOOOOOOOOOO!!!! GaYs! Help me!
I need to find new Windows 
give reference please
[http://kudapoyti.com.ua](http://kudapoyti.com.ua)

---

### Post by nioakeim on 2007-05-23
Same problem here with a Kworld PVR-7130. The strange thing is that i installed TvTime and after some playing aroung i connected a camera in the composite input and i got picture. The tuner though was dead...
Any valuable help?

---

