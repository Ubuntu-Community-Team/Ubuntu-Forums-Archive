---
title: "Hdhomerun IR Set Up Help Needed"
date: 2008-06-20
forum: Mythbuntu
---

### Post by gmwouters on 2008-06-20
I could really use some help setting up the IR portion of the Silicon Dust HDHomeRun.  I went to Silicon Dust's website and started following the instructions under LIRC (IR remote control support). 

I did:

[COLOR="DeepSkyBlue"]1) Configure the HDHomeRun to send IR commands to LIRC:

	hdhomerun_config <device id> set /ir/target"<ipaddress>:5000 no_clear"[/COLOR]

using the ip address and device id I got from running "hdhomerun_config discover"


Next tried to run the following code:

	[COLOR="DeepSkyBlue"]2) Run irrecord in UDP mode, this will generate a configuration file in the current 	directory. (note: lircd must not be running)

	irrecord -H udp -d 5000 "<name of remote>"[/COLOR]

I start pushing buttons on the remote when the program prompted me to, and it kicks me out of the program after 10 seconds. The program says something like no signals were received.  I have tried a couple different remotes that I know are working, so I don't think it is the remote.

Here are my questions: 	
a)  Should I see some thing happen after I run the command line after [COLOR="DeepSkyBlue"]"1)"[/COLOR] ?  Also do I put in the quotation marks ("") when I put in the command line?  (Sorry I am new to Linux)
b)  How do I stop lircd as it says in [COLOR="DeepSkyBlue"]"1)"[/COLOR] and also how do I tell if lircd is even running?
c)  How do I make irrecord work?  I guess this is really the heart of the problem.  I am not sure what to do after I run the command line after [COLOR="DeepSkyBlue"]"2)"[/COLOR] and nothing happens. 
d)  Is there something I can do diagnose the problem?

I would really love to get the ir portion of the HDhomerun working.  Any help would be greatly appreciated.

---

### Post by Dewey_Oxberger on 2008-06-22
Wow, been a while since I set mine up (and I don't use it any more, We all like just using a Logitech wireless keyboard - biggest remote you ever saw).  :)

The device id should be printed on a label on the bottom of the HDHomeRun.

Loads of lirc info in the documentation section of their website:

[http://www.lirc.org/](http://www.lirc.org/)

You should check their website for the lircrc files.  Odds are you don't need to irrecord your own file, there probably is one up there that will work for you.

That said, as I recall I used irw (maybe) to test the setup.

Finally, the HDHomeRun's ir receiver is very directional, you have to aim right into the black bar on the front of it (it has lousy sensitivity - that's the only thing I don't like about it).

---

### Post by gmwouters on 2008-06-22
Dewey,

Thanks.  I will check out [www.lirc.org](www.lirc.org).  I did not know about he directivity of the IR receiver on the HDHomeRun, but I will try to point it right at the black bar.

---

### Post by knowtown on 2008-12-25
I am also having trouble getting a remote to work with mythbuntu using the hdhomerun. I have followed all the instructions on the silicon dust website and can successfully run all the commands there but when I go to irw to verify nothing happens. I can run irrecord so I know that the remote is talking to the hdhomerun box but I get nothing after that. there is a lirc.conf file for my remote (Sony RM-V210) at the lirc website so I copied that to /etc/lirc/lircd.conf but still nothing. I have tried mythbuntu-lirc-generator which says it creates the files I need but nothing works. I have found a lot of great sites that help with people who are using usb or serial remotes but nothing about network udp. It seems that mythbuntu has lirc related files scattered all over the place and I am not sure which I need and which I don't and where everything is supposed to live. 

I can get irrecord to work.

I can get gnome-lirc-properties to work but not save the custom file.

I can get mcc to point to the conf file for my remote in /usr/share...

But none of these three options get me to a functioning remote in myth.

So I know that there is some communication taking place between my remote and the hdhomerun and the computer but I cannot get any remote to actually work with myth. If anyone has any idea on how to get this working and wants to throw another bone at this thread I would really appreciate it. The remote is the last thing I need to get working to win over the family and keep me from pulling my hair out.

Thanks!

---

### Post by knowtown on 2009-01-03
Well, I started from scratch and I have made a little bit of progress getting my Sony RM-V210 Universal Remote control working with the HDHomerun infra red receiver and talking to the computer via udp. I can now get irw to respond to my remote everytime, even after reboots and all the buttons from my lircd.conf file for the Sony remote are displayed correctly there. So I am sure I am getting close.

Now, if anyone out there in the wide world of mythbuntu users can help me get the remote working with MythTv that would be great. The only thing I have tried now that irw is working every time is running the mythbuntu-lircrc-generator which reports that it ran successfully but I could still not control MythTv with the remote. I rebooted for good measure but still no joy. So if everything is working with irw, what is still needed to get MythTv to recognize remote control commands? Anyone?

Thanks in advance to anyone who can shed some light on this for me!

---

### Post by knowtown on 2009-01-05
OK, I finally got it so no need for any replies. Everything was working correctly I just did not know it because the buttons I was pressing primarily to test from the main MythTv window (the arrow buttons) were not yet in the lircrc file. I went through and manually added all the buttons from my lirc.conf into my lircrc and viola! everything is working. Still need to tweak a few buttons but I am happy to finally be using the remote with Mythbuntu and HDHomerun.

Thanks everyone in this thread for getting me on the right track.

---

