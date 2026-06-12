---
title: "firewire connection to SA 8300HD"
date: 2007-11-02
forum: Mythbuntu
---

### Post by steve_baker on 2007-11-02
i am trying to connect my laptop running ubuntu 7.10 with mythbuntu added to my cable receiver. the SA 8300HD has 2 firewire ports, both of which register as a good connection...

```

# plugreport 
Host Adapter 0
==============

Node 0 GUID 0x0090f500004c9518
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x0014f86e7a100000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=1, data_rate=1, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

```

but when i try to test the connection it always fails. i have the receiver set to a  broadcasted channel i am assuming is not encrypted and have tried this on both firewire ports (rebooting when switching just to make sure)

```

# ./firewire_tester -p -P 0 -n 1 -r 5
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed

```

and 

```

# ./firewire_tester -B -P 0 -n 1
Action: Attempt to fix broadcast connection 1 times, node 1
Broadcast: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
Broadcast Fix: Failed

```

i have tried things like:

```
# plugctl -n 1 oPCR[0].bcast_connection=1
```

as well to no avail. i haven't been able to find any documentation on what to do when the connections just fail every time and am hoping someone can point me in the right direction.

the long term plan is to use a different machine than my laptop to set all this up so let me know if it would help to do a clean install from the 7.10 install disk on the real machine i am going to use.

TIA

---

### Post by ickyb0d on 2007-11-02
I actually had this exact same problem.  According to the FCC your cable provider must provide you with an enabled firewire port (on an HD cablebox) upon your request.  So my first question is... did you request that?  Since you're actually getting a reading using plugctrl, I assume it IS enabled.

Now the part I had to figure out on my own - is that the cable company in reality only should broadcast the over the air stations, and any non-free channels they have the right to encrypt.  I get the same results on my firewire connection when i'm on a non-free channel (i.e. cartoon network, G4, or anything i couldn't pick up with an antenna).  Try switching your cablebox to a known over-the-air channel and see if p2p works.  Mine works 100% of the time on those channels when connecting p2p.

You may also want to take a look at the [documentation](https://help.ubuntu.com/community/MythTV_Firewire) and see if you need to add some sort of firewire "primer" script as well.  But my initial guess is that you just have your box tuned to a non-free station.

---

### Post by steve_baker on 2007-11-02
thanks for the help.

i didn't request a firewire enabled box. i too was assuming that the output from plugreport was a confirmation that the firewire is active. does anyone know if that is an unsafe assumption?

i tried channel 9 which is FOX where i live. i am pretty sure that it is a freely available over the air channel but i will try to confirm that tonight when i get home.

i haven't set up a primer yet because i haven't actually gotten to the point where i have setup the capture in mythTV. i figured if firewire_tester is failing every time that it wouldn't do any good to try yet. i do plan on setting up the primer as documented in the setup when i get everything running though.

a guy at worked asked me today if it would help to reboot the cable box now that the firewire is connected. i hadn't thought of that, i had only rebooted my laptop. i am going to try to reboot the cable box tonight to see if it helps.

thanks,

steve

---

### Post by dmfrey on 2007-11-02
I have had very varying experiences with Firewire.  Your best bet is to shutdown your machine, unplug the stb for 30 seconds or so and plug it back in, then power on your laptop.

After all of that is done, run plugreport again.  You may find that your default node is different than what you have been seeing.  Mine, for instance, is 2, but, periodically, it will just up and switch on its own to 1 or 0.  I have found that heat can be cause of this.  Once all of this is done, try the firewire tester to see if you get any connection.

I hope this helps.

Dan

---

### Post by WhyWontThisWork on 2008-02-19
has there been a solution to this problem? im looking to do the same thing
-J

---

### Post by theacoustician on 2008-02-19
If you don't specially ask for a box with firewire enabled, don't expect it to be hot.  Even if the port is on there, the likelyhood that its active without you asking is low.

---

### Post by newlinux on 2008-02-19
Also, some providers in some areas put 5c content protection on every channel (whether they are supposed to or not), which would give you this result as well. In my area, they even do it on a show by show basis (football games on the local networks have had 5c content protection turned on but other programming on the same stations do not). Do the SA have a diagnostic screen where you can check the 5c setting like the Motorolas do?

---

### Post by majoridiot on 2008-02-19
in my experience, many SA boxes will show "valid" firewire connections on both stb ports with plugreport
but only one is fully active- so be sure to test both ports before assuming there is a problem.

in cases where both ports show valid connections but fail upon testing, the two most likely causes are:


that the ports aren't fully enabled- in which case your cable company should enable at least one to 
comply with FCC regs- or, more likely, your cable company is incorrectly setting the CCI flag to 0x02,
in which case you are most likely out of luck.  this happened to me and there's really no way to get
them to comply with the law.

---

### Post by kameleon25 on 2008-02-19
I too am wondering about this. I use Comcast in the central MS area. I have not gotten to the testing phase yet to even see if the ports are "seen" on my mythtv box but plan to do that tonight hopefully. I am not too concerned about the HD stuff at the moment but mostly the channels above "standard teir" because that is where my cable company moved all the "good" discovery channels. If I cannot get the firewire to work I will have to look into getting a second pvr-500 to use with a seperate cable box specifically for those channels. That would not be ideal though. I will post my findings.

---

### Post by dannyboy79 on 2008-02-19
i have a SA3250HD and I can capture local channels thru firewire just fine. Im in Milwaukee, WI on Time Warner Cable HD package. The problem I had was/is that the channel changing doesn't/didn't work. Then the next problem was that I couldn't figure out how to get the digital lineup from  schedules direct to only have the channels I get over firewire but then also have a second one that would allow ALL digital channels which I capture from the STB over s-video into a PVR-350. So I gave up on firewire, I am not an HD fanatic so the HD downgraded throught the s-video is fine for me. I can even capture HBO and ALL channels I subscribe to that's the awesome part. I use a serial ir-blaster to control the STB and with the help of another person with this box, he helped me with a bash script that checks to make sure the STB is on and if not, it turns it on, then changes to the correct channel to start recording. For some reason I was noticing my cable box being off despite me not even touching it. Maybe Time Warner sent an update that makes it shut off. Anyway, here's the website that talks all about it.
[http://evuraan.blogspot.com/2008/01/how-to-ensure-set-top-box-stb-is.html](http://evuraan.blogspot.com/2008/01/how-to-ensure-set-top-box-stb-is.html)

---

### Post by pastafazoule on 2008-02-22
i am trying to capture hd from my tw 8300 box to my mac  my mac can see the 8300 but there is nothing streaming out,they have the cci set to once,so now tw in central ny is saying because the mac is not dtcp compliant that they have a right to block all the hd channels even over the air networks,can they do this

---

### Post by majoridiot on 2008-02-26
> **pastafazoule said:**
> i am trying to capture hd from my tw 8300 box to my mac  my mac can see the 8300 but there is nothing streaming out,they have the cci set to once,so now tw in central ny is saying because the mac is not dtcp compliant that they have a right to block all the hd channels even over the air networks,can they do this

no, they are not supposed to- but yes, because the FCC lets them get away with it.  :confused:

---

### Post by mickeybeau on 2008-02-27
Hi 
2 weeks ago i was able to record from  XBUNNTU 7 on the firewire port.
Broadcast did not work but P2P was ok and the video capture SD HD was good. For whatever reasons it stopped  (last week) the P2P connection is always failing now. 

But if i connect the firewire cable to my XP machine, it is capturing
(with a lot of pixelisation) for the HD program) but it is capturing...

So i have reinstall XUBUNTU reinstall the proper libraries, but firewire_tester always says that the P2P failed. And test-mpeg2 produce files wth 0 bytes.

I am at lost here , why am i capturing in XP and not in Linux????

help Please
Thanks
Michel

---

### Post by theacoustician on 2008-02-28
> **mickeybeau said:**
> Hi 
2 weeks ago i was able to record from  XBUNNTU 7 on the firewire port.
Broadcast did not work but P2P was ok and the video capture SD HD was good. For whatever reasons it stopped  (last week) the P2P connection is always failing now. 

But if i connect the firewire cable to my XP machine, it is capturing
(with a lot of pixelisation) for the HD program) but it is capturing...

So i have reinstall XUBUNTU reinstall the proper libraries, but firewire_tester always says that the P2P failed. And test-mpeg2 produce files wth 0 bytes.

I am at lost here , why am i capturing in XP and not in Linux????

help Please
Thanks
Michel
Do you have the permissions properly set on your firewire port?

---

### Post by dannyboy79 on 2008-02-28
also, do you have the channel set on a "free" channel, like NBC or ABC. Anything that is not encrypted or that doesn't have a copy flag set on it.

---

### Post by majoridiot on 2008-02-28
did you follow the guide at all, which covers all of the "did you's?" that keep being repeated over and over? ;)

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

---

### Post by mickeybeau on 2008-02-28
Hi,

 thanks for the fast answers guys.


First, i have the proper permissions,the device
CRW_R__R__ /dev/raw1394 has a group owner of DISK 
so i  have added my user to that group. Plugreport will fail otherwise

Also to make sure , i su to root to run the plugreport and the firewire tester.

I am trying to capture recorded programs on my 8300HD so it shall work
it was working before.

If i switch on the windows XP side , i can capture the recorded programs not the live ones.



when i start a recorded program on my8300hd, i am starting the firewire_tester and the P2P test always fails (0 packets received)

Bye
michel

---

### Post by majoridiot on 2008-02-28
> **mickeybeau said:**
> I am trying to capture recorded programs on my 8300HD so it shall work
it was working before.

If i switch on the windows XP side , i can capture the recorded programs not the live ones.

when i start a recorded program on my8300hd, i am starting the firewire_tester and the P2P test always fails (0 packets received)

Bye
michel

unfortunately, what you are describing sounds a lot like either the firewire port on the stb
has been disabled or partially crippled by your cable company, or they enabled encryption on the
channels.  that's what happened in my case- one day it worked, the next they had changed CCI to
0x02 on most channels.

my only other thought is if there is more than one firewire connector on the stb, try swtiching
the cable to that one.  if you do this with the computer and stb turned on, you will most 
likely need to reset the firewire bus (-R switch with firewire_tester) or reboot the computer.

---

### Post by dannyboy79 on 2008-02-29
woooooo, now you're saying that you're trying to capture a file that was already recorded by your 8300HD DVR? we don't even know if the STB outputs a recorded show out the firewire port. at least I don't anyway. the way I have gotten flicks off my dads sa8300hd is by hooking up an EyeTV and I just used the component out on the STB into the EyeTV and from the EyeTV was a firewire cable. Does your P2P connection work if you tune the STB to a known "local" channel and run firewire_tester? Are you saying that Windows XP can capture a video that's being played from the STB DVR thru firewire? If that's the case than I guesss we know that the stream from teh DVR is being fed out the firewire port but I also wonder if it matters the channel of the recording. If the channels has a copy flag set to 1 and your DVR already captured it, that's it, you can't copy it again. BUt if you tried a different channel that had a different copy flag set when you were using Windows than that would explain that. ANyway, I can't help anymore. Good luck

---

### Post by majoridiot on 2008-02-29
> **dannyboy79 said:**
> woooooo, now you're saying that you're trying to capture a file that was already recorded by your 8300HD DVR? we don't even know if the STB outputs a recorded show out the firewire port

if the program had a CCI of 0x00 (copy freely), then it will output just fine over firewire for
archiving purposes... and to help keep the dvr's tiny hard drive clean. ;)

if the program had a CCI of 0x02, or copy once, then you will not be able to play it back and 
record it via firewire- as the dvr would have set the CCI of the program to 0x01 or 
copy never, per the DTCP specification.

this is what leads me to suspect his CCI has been locked down- if he can not record any channels
but can record previously recorded- and most likely CCI 0x00- programs, then that means there
is nothing wrong with the firewire, but the stream itself.

---

### Post by mickeybeau on 2008-03-05
Hi,

I guess i was not clear.

I am trying to extract pre-recorded programs from the 8300HD
when i do that 
-  the windows system sees the stream 
-   but the xubuntu does not see the stream

To me that proves that there is a problem with the firwire on the xubuntu system

Thanks
michel

---

### Post by mickeybeau on 2008-03-05
Also

I have the same result from a ubuntu 7.X system running
on a SPARC  ULTRA 10 with a PCI firwire card

the SPARC does not see the stram either

Bye
michel

---

### Post by Joshua on 2008-06-24
I just got an SA 8300HD.  I found out that if you hold the "Select" button down for a couple seconds (until the mail icon starts flashing) and then hit the "Info" button you can get into a system status area.

1 - Are there any screens in that system status area that I can use to reliably confirm that my firewire (1394) ports are active?

2 - If I turn my computer off, plug in the firewire cable to the STB, and turn the computer back on, and plugreport always gives something like:
```
Host Adapter 0
==============

Node 0 GUID 0xf4bff0b7b7f0bff4
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR
```
on both ports, does that mean that my firewire ports are not active?  And is that process reliable enough to go ahead an call my cable company to complain, and file complaints with the FCC and attorney general, etc.?

---

### Post by majoridiot on 2008-06-24
> **Joshua said:**
> I just got an SA 8300HD.  I found out that if you hold the "Select" button down for a couple seconds (until the mail icon starts flashing) and then hit the "Info" button you can get into a system status area.

1 - Are there any screens in that system status area that I can use to reliably confirm that my firewire (1394) ports are active?

each stb is different, so maybe another 8300 owner will chime in on specifics... but you are 
looking for anything referring to "1394 port status" or something similar.


> **Joshua said:**
> 2 - If I turn my computer off, plug in the firewire cable to the STB, and turn the computer back on, and plugreport always gives something like:
```
Host Adapter 0
==============

Node 0 GUID 0xf4bff0b7b7f0bff4
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR
```
on both ports, does that mean that my firewire ports are not active?  And is that process reliable enough to go ahead an call my cable company to complain, and file complaints with the FCC and attorney general, etc.?

this is a pretty good indication that the firewire ports are not active.  if they were, you 
should see a node with a good GUID and plug status and an empty node, as you are 
seeing now.

although i do *heartily* encourage filing all of the necessary complaints, i think you 
also need to be aware that by all reports, the 8300 series stb outputs mangled transport
streams over firewire for every channel except the one used to view pre-recorded dvr 
content.  in other words, it is pretty much **useless** for use with mythtv firewire connections.
i worked at length with another mythbuntu 8300 owner to try and determine what was 
going on, and *none* of a dozen professional video tools could make sense of the stream. 
other than the synch byte and a few other parts of the mpeg header, it appeared to be 
garbage.

note that the stream was not encrypted- it was clear, just invalid.

this complaint is not limited to mythv- it is also well documented in windoze-land and across
multiple cable providers.  it appears that this crippling of firewire output for regular channels is
either intentional, or a convenient "bug" in the stb firmware that nobody is in a hurry to fix.

thought you should know before this becomes too large of a frustration for you... ;)

---

### Post by Joshua on 2008-06-24
> **majoridiot said:**
> each stb is different, so maybe another 8300 owner will chime in on specifics... but you are looking for anything referring to "1394 port status" or something similar.

I did see some screens that had some info but I couldn't tell what some of the info meant.  Maybe I'll take some pictures tonight and post them here.  It looked like the important fields all said unavailable or disabled, but others had some numbers in them.

> **majoridiot said:**
> this is a pretty good indication that the firewire ports are not active.  if they were, you should see a node with a good GUID and plug status and an empty node, as you are seeing now.

Oh well.  Does anyone know if the 8500HD is any better?  I'm in Alexandria, Virginia and I have Comcast.  I actually started with an 8000HD, then upgraded to the 8500HD, and then was told that the 8500HD was too new.  So they gave me the 8300HD, (saying, "Oh, this is deffinately the one you need!" - yeah right) but noone on the phone ever actually knows what I'm talking about when I mention the firewire port.  ("Is the box plugged in?" "I resent your authorization, does it work now?" "What's on fire?" - That's all I get.  I hate Comcast).

> **majoridiot said:**
> although i do *heartily* encourage filing all of the necessary complaints, 

Nothing will change if we don't complain about it.  This seems like one of the few times the FCC is working FOR consumers.  We should jump on it.

> **majoridiot said:**
> i think you also need to be aware that by all reports, the 8300 series stb outputs mangled transport streams over firewire for every channel except the one used to view pre-recorded dvr content.  in other words, it is pretty much **useless** for use with mythtv firewire connections.

This would actually not be too bad for me.  It's not ideal, but there are certain things that I just want to get off the box without buying any new computer stuff.

> **majoridiot said:**
> i worked at length with another mythbuntu 8300 owner to try and determine what was going on, and *none* of a dozen professional video tools could make sense of the stream. other than the synch byte and a few other parts of the mpeg header, it appeared to be garbage.

note that the stream was not encrypted- it was clear, just invalid.

this complaint is not limited to mythv- it is also well documented in windoze-land and across multiple cable providers.  it appears that this crippling of firewire output for regular channels is either intentional, or a convenient "bug" in the stb firmware that nobody is in a hurry to fix.

thought you should know before this becomes too large of a frustration for you... ;)

I appreciate the "heads up!"  It IS getting very frustrating.  Comcast is completely useless (except that they haven't given me a hard time for trading in three boxes so far this week - they give me almost any equipment that I ask for).  The technical support can't even tell me if the firewire is active or not.  Again, do you know if the 8500HD is any better?

Also, I guess this is a little off topic, but I've got the pcHDTV3000 (two of them).  It should be able to get the unencrypted channels right from the cable, but when I hook everything up, they come in choppy.  Has anyone else had this problem?  I'll still have the firewire fight with Comcast, but I thought it would be nice to watch something on the computer in the meantime.

---

### Post by majoridiot on 2008-06-24
> **Joshua said:**
> Oh well.  Does anyone know if the 8500HD is any better?  I'm in Alexandria, Virginia and I have Comcast.  I actually started with an 8000HD, then upgraded to the 8500HD, and then was told that the 8500HD was too new.  So they gave me the 8300HD, (saying, "Oh, this is deffinately the one you need!" - yeah right) but noone on the phone ever actually knows what I'm talking about when I mention the firewire port.  ("Is the box plugged in?" "I resent your authorization, does it work now?" "What's on fire?" - That's all I get.  I hate Comcast).

i couldn't find any info readily available specifically for an "8500", but the 8500 series all
have firewire ports and might be worth a shot.  here is a link to that series:

[http://www.cisco.com/en/US/products/ps8613/products_data_sheets_list.html](http://www.cisco.com/en/US/products/ps8613/products_data_sheets_list.html)

you will get **nowhere** calling customer support.  you will need to get a tech there on-site and
address the issue with them.  from there, they can check with the CO, etc. and find out what the deal is.
the signals needed to enable the ports come from the head end at the CO and i can guarantee you will not
find a fix-the-problem-by-working-a-checklist customer service rep that will either understand, or be
able to fix it if you do.

having been where you are now (with a motorola box), i can tell you that you will need to educate the
service tech a little... specifically that comcast is *required* by law to have active ports
on stbs that are firewire capable.  if you are trading these in, in-person, ask to speak to a technician
or an engineer at the office.  you may need to schedule a service call to have one come to the house, but
that is the best way to address this.

if you ever want to use the firewire function with mythtv for pvr-type recording, stay away from the 8300 for
sure.

comcast has (surprisingly) improved firewire support across the board and is one of the better cable 
providers when it comes to firewire support on their stbs.

be **grateful** you are not a TWC customer... ;)

---

### Post by Joshua on 2008-06-24
> **majoridiot said:**
> comcast has (surprisingly) improved firewire support across the board and is one of the better cable 
providers when it comes to firewire support on their stbs.

be **grateful** you are not a TWC customer... ;)

I KNOW!  I've read lots of posts from Comcast customers in other parts of the country, and they seem to get a reasonable amount of cooperation.  I didn't think this was going to be such a pain.  I think I'll take your advice and bring the 8300 back tonight, again :-), and ask for the 8500 and a real technitian.  Oh, and I'll take a couple pictures of the system status screens on both of the STBs.  Maybe someone will find them useful.

---

### Post by majoridiot on 2008-06-24
> **Joshua said:**
> I KNOW!  I've read lots of posts from Comcast customers in other parts of the country, and they seem to get a reasonable amount of cooperation.  I didn't think this was going to be such a pain.  I think I'll take your advice and bring the 8300 back tonight, again :-), and ask for the 8500 and a real technitian.  Oh, and I'll take a couple pictures of the system status screens on both of the STBs.  Maybe someone will find them useful.

pictures of the status screens would be very helpful.

i'm a new comcast customer... they bought out my local provider and took over this year.  after the
takeover, the vast majority of channels that were previously encrypted (about 95% of the "digital
tier" channels) had the encryption removed and are now clear for recording.  approximately 95% of my
total channels are now either entirely unencrypted or are conditionally encrypted, depending on
the program.  only a handful of channels (like my local NBC-HD and TNTHD) are always encrypted.  you can imagine my amazement that mega-provider comcast cleared the channels the local refused to.

good luck at the office!

---

### Post by Joshua on 2008-06-24
Well, I didn't have much luck with the Comcast office tonight.  I've still got the 8300, and there wasn't anyone in the office with the knowledge or authority to help me, but a technician is supposed to try to figure it out and call me tomorrow.  Normally I wouldn't have really thought much of a promise like that, but he gave me his phone number.  So I can call him if he doesn't call me.  :-)

Also, I know this is an Ubuntu forum, but I tried to get the Firewire to work in the Windows partition.  Previously, I was able to get the computer to recognize that it was connected to something, and even change the channels, but now it won't even recognize it.  I can't find any uninstall/reinstall buttons and drivers keep failing.  Is there any good, recent information out there on how to get the Firewire link to work in Windows without already having a tuner card, and without spending any money?

I posted some pictures of my [8300 menus(http://ubuntuforums.org/album.php?albumid=295)]("http://ubuntuforums.org/album.php?albumid=295"), too.  I think those are the only two relevant ones.  If anyone wants to see all of the screens, just let me know, and I'll upload them.

---

### Post by majoridiot on 2008-06-25
> **Joshua said:**
> Well, I didn't have much luck with the Comcast office tonight.  I've still got the 8300, and there wasn't anyone in the office with the knowledge or authority to help me, but a technician is supposed to try to figure it out and call me tomorrow.  Normally I wouldn't have really thought much of a promise like that, but he gave me his phone number.  So I can call him if he doesn't call me.  :-)

the techs are usually the best guys to deal with, when you can.  they usually know what is going
on, or are willing to find out if they don't.

> **Joshua said:**
> Also, I know this is an Ubuntu forum, but I tried to get the Firewire to work in the Windows partition.  Previously, I was able to get the computer to recognize that it was connected to something, and even change the channels, but now it won't even recognize it.  I can't find any uninstall/reinstall buttons and drivers keep failing.  Is there any good, recent information out there on how to get the Firewire link to work in Windows without already having a tuner card, and without spending any money?

although the thread is old, this one has been the gold-standard in the windoze firewire world for 
drivers and info:

[http://www.avsforum.com/avs-vb/showthread.php?s=&threadid=403695](http://www.avsforum.com/avs-vb/showthread.php?s=&threadid=403695)

except...

> **Joshua said:**
> I posted some pictures of my [8300 menus(http://ubuntuforums.org/album.php?albumid=295)]("http://ubuntuforums.org/album.php?albumid=295"), too.  I think those are the only two relevant ones.  If anyone wants to see all of the screens, just let me know, and I'll upload them.

the first picture shows firewire outputs are disabled.  there is also no policy info for it,
which leads me to believe the ports are totally inactive.  the tech should be able to work
with the chief engineer at the head to enable it.

good luck... :)

---

### Post by Joshua on 2008-07-09
Well I finally got some answers from Comcast.  They said that the only box they provide with Firewire access in northern Virginia is the 3250 (don't know what that means) but it's not a DVR.  So I can go in and request that box, but:

1 - She said that they are only required to have at least one box with Firewire available.  So the 3250 non-dvr is my only option.  How will I live without time-shifting?

2 - I won't be able to get any of my basic cable channels on the 3250, just digital ones, and I believe there are a couple channels that are only available in the basic lineup (Cartoon Network comes to mind as one of them).  So I might not be able to watch Futurama.

3 - I won't be able to use the On Demand services.

4 - The stream somehow obeys the copy protection so hooking it up to a computer won't work.  They specified a TV will work but a computer won't.

The first three make sense to me, technically.  It sucks that the cable company does stuff like that, but they're evil corporate pigs, so at least it makes sense.

But for the fourth one - if there is some sort of encryption scheme then a TV won't be able to use that signal either, right?  What kind of copy protection would work on a TV, but not on a computer?

---

### Post by majoridiot on 2008-07-09
> **Joshua said:**
> Well I finally got some answers from Comcast.  They said that the only box they provide with Firewire access in northern Virginia is the 3250 (don't know what that means) but it's not a DVR.  So I can go in and request that box, but:

1 - She said that they are only required to have at least one box with Firewire available.  So the 3250 non-dvr is my only option.

2 - I won't be able to get any of my basic cable channels on the 3250, just digital ones, and I believe there are a couple channels that are only available in the basic lineup (Cartoon Network comes to mind as one of them).  So I might not be able to watch Futurama.

3 - I won't be able to use the On Demand services.

4 - The stream somehow obeys the copy protection so hooking it up to a computer won't work.  They specified a TV will work but a computer won't.

The first three make sense to me, technically.  It sucks that the cable company does stuff like that, but they're evil corporate pigs, so at least it makes sense.

But for the fourth one - if there is some sort of encryption scheme then a TV won't be able to use that signal either, right?  What kind of copy protection would work on a TV, but not on a computer?

keep your 8300 for DVR use and get a 3250 for mythtv use and 1, 2 and 3 are moot points. ;)  
they probably wouldn't hit you for more than $6-8 a month for it.

as to 4: they are talking about DTCP (or 5c) encryption.  comcast is actually one of the better
providers, when it comes to not encrypting every channel in sight... e.g. my comcast has
approximately 90% of the channels clear- or unencrypted.  another mythbuntu'er with comcast on
the east coast reports similar luck.

you could try looking/asking in places like AVS forums to see if you can get a report on the
status of firewire encryption in your area... or just get the 3250 for a month and try it
out.  you can use scanfw to survey the encryption status of your line-up.

never trust customer service reps when discussing firewire... 99.9% of the time, they have
no clue what they are talking about.

---

### Post by kameleon25 on 2008-07-09
> **Joshua said:**
> Well I finally got some answers from Comcast.  They said that the only box they provide with Firewire access in northern Virginia is the 3250 (don't know what that means) but it's not a DVR.  So I can go in and request that box, but:

1 - She said that they are only required to have at least one box with Firewire available.  So the 3250 non-dvr is my only option.  How will I live without time-shifting?

2 - I won't be able to get any of my basic cable channels on the 3250, just digital ones, and I believe there are a couple channels that are only available in the basic lineup (Cartoon Network comes to mind as one of them).  So I might not be able to watch Futurama.

3 - I won't be able to use the On Demand services.

4 - The stream somehow obeys the copy protection so hooking it up to a computer won't work.  They specified a TV will work but a computer won't.

The first three make sense to me, technically.  It sucks that the cable company does stuff like that, but they're evil corporate pigs, so at least it makes sense.

But for the fourth one - if there is some sort of encryption scheme then a TV won't be able to use that signal either, right?  What kind of copy protection would work on a TV, but not on a computer?

Good info. I think I may try my luck with this one also. I do not care that it doesn't have a built in DVR as I will be hooking this up to my mythtv box anyways. This is a cheaper route than buying another PVR-500... .MUCH cheaper. As for the not being able to get the lower "non-digital" channels that kind of makes sense but then again it don't. And if you can hook it up to a tv and it output fine then you should be able to hook it up to a pc and it output fine. Unless there is some special tv that has a firewire chipset that does some magic.

---

### Post by Joshua on 2008-07-09
> **majoridiot said:**
> keep your 8300 for DVR use and get a 3250 for mythtv use and 1, 2 and 3 are moot points. ;)  
they probably wouldn't hit you for more than $6-8 a month for it.
Yeah, I'll probably do that and try it out for a month just to tinker.  I just don't like that fact that they are restricting me to a specific box and that I have to pay more for it.  They're making this sooooo complicated!  They could just activate it on the box I have!
> **majoridiot said:**
> as to 4: they are talking about DTCP (or 5c) encryption.  comcast is actually one of the better
providers, when it comes to not encrypting every channel in sight... e.g. my comcast has
approximately 90% of the channels clear- or unencrypted.  another mythbuntu'er with comcast on
the east coast reports similar luck.
Oh.  Well if that's the case then the lady on the phone must have been saying that the encrypted channels won't work and she probably just didn't realize that they would at least provide local channels in the clear.  (Or maybe it's some sort of scare tactic because they don't like people hooking computers up to their system.)  I'm still not sure I understand it, though.  TVs don't come with the ability of decrypting 5c do they?  Wasn't the Firewire port requirement originally intended for hooking to a Firewire port on a TV?

I don't think my area is 90%, but you're right that it's much more than just local channels.  My PCHDTV 3000 doesn't scan QAM well but even with the bad reception and the choppy channels, I get more than just local right off the cable.  (By the way, the 3000 QAM reception is the reason I'm looking into the Firewire port in the first place.  If anyone has a surefire way of fixing that, please let me know.  I hear it's usually related to unstable voltage coming from the PCI sockets, and I'm not sure how to fix that.)
> **majoridiot said:**
> you could try looking/asking in places like AVS forums to see if you can get a report on the
status of firewire encryption in your area... or just get the 3250 for a month and try it
out.  you can use scanfw to survey the encryption status of your line-up.
Yup, I'll probably tinker with it for a while while I keep working on getting them to turn it on for the DVR.
> **majoridiot said:**
> never trust customer service reps when discussing firewire... 99.9% of the time, they have
no clue what they are talking about.
OH! That's one of the best parts, actually.  I'm no longer talking to the 800 customer service line.  After about 3 weeks of back and forth, I finally got the corporate number and then the number for a lady in the northern Virginia executive office.  So I've been working with her.  She's actually pretty helpful, even though it takes her a long time to get back to me with technical answers, so maybe "evil corporate pig" is a little harsh.  But still, this process really shouldn't take three weeks.

---

### Post by Joshua on 2008-07-09
> **kameleon25 said:**
> And if you can hook it up to a tv and it output fine then you should be able to hook it up to a pc and it output fine. Unless there is some special tv that has a firewire chipset that does some magic.
Exactly!  I don't get it.  She said she'd go back and try to clarify with their technicians.  So I'll let you know what I hear... it'll probably take a couple days.

---

### Post by majoridiot on 2008-07-09
just to clarify things a little... "5c", or DTCP encryption was developed
especially for this type of application and was implement first (AFAIK) on
firewire.  what the rep told you is, in essence, correct... a "non-compliant"
device like a computer will be unable to view/record 5c encrypted content,
where a compliant device, like a tv, will.

firewire inputs on tvs are, and always were, very rare.  i don't know
of a model currently in production that has it... not to say that there 
is not.  firewire from stbs was most exploited by HD-DVHS decks (i have
2).  they record encrypted content without a problem, as they are
"DTCP compliant".

the point was summed up in total by the statement "they don't want you
hooking your pc up to their boxes".  

they do not.  *period.*

this is nothing new in the land of "fair-use".  fighting for the simple right 
to time-shift programming on the device of *your* choice began with 
BETAMAX and will likely never end.

---

### Post by Joshua on 2008-07-10
> **majoridiot said:**
> just to clarify things a little... "5c", or DTCP encryption was developed
especially for this type of application and was implement first (AFAIK) on
firewire.  what the rep told you is, in essence, correct... a "non-compliant"
device like a computer will be unable to view/record 5c encrypted content,
where a compliant device, like a tv, will.
I just had a thought about the 5C encryption.  Is it carried in the signal on the cable from the company, or is it implemented in the box so that it only affects the Firewire and other ports on the back?  I ask because I wonder if the number of unencrypted channels that I can get with my pcHDTV 3000 (right off the cable) has any bearing on the number of channels I'll get on the Firewire port (through the STB).

---

### Post by newlinux on 2008-07-10
> **Joshua said:**
> I just had a thought about the 5C encryption.  Is it carried in the signal on the cable from the company, or is it implemented in the box so that it only affects the Firewire and other ports on the back?  I ask because I wonder if the number of unencrypted channels that I can get with my pcHDTV 3000 (right off the cable) has any bearing on the number of channels I'll get on the Firewire port (through the STB).

5c is for the firewire output. What channels are QAM encrypted don't necessarily correspond to which channels are 5c copy protected. They are separate implementations. A channel can be encrypted over QAM but have 5c (CCI) settings that allow it to be recorded freely over firewire and vice versa. My available QAM stations and firewire stations are different. Also not that 5c encryption can be turned on program by program, not just channel by channel. Comcast has done this a few times in my area. QAM and firewire availability vary greatly between providers, and withing providers from region to region.

---

### Post by majoridiot on 2008-07-10
> **newlinux said:**
> Also not that 5c encryption can be turned on program by program, not just channel by channel. Comcast has done this a few times in my area.

this is very true, and unfortunately, also very common.  on my cable system, two channels that
are notorious for this are TVLAND and SCIFIHD.  to complicate matters, i have also seen encryption
turned on and off *within* programs, when they go to commercials- i.e. the program is
encrypted, but the commercials are not.  strangely enough, i have also seen instances where the program
was clear, but a commercial within the block was encrypted- which would kill a recording.

this is one reason scanfw incudes the -w option, which does nothing but watch the CCI encryption
bits and log the time and date as they change.  on particularly problematic channels, the output is
quite interesting for long (12-24hr) runs.

---

### Post by newlinux on 2008-07-10
Yes, I think I'll use scanfw and see whats what. I don't use my firewire connection a lot, but I first discovered they were doing this program by program when some recordings were failing and some wheren't on the same channels. scanfw will help me "profile" the channels I really care about.

Thanks.

---

### Post by kameleon25 on 2008-07-16
Is it possible to use the firewire only to change the channels and still output the video through the composite? I ask because I am going here in a few minutes to grab a 3250 (or similarly firewire enabled box) to test with. Since I have firewire it is cheaper to do that than buy the IR stuff.

---

### Post by majoridiot on 2008-07-16
> **kameleon25 said:**
> Is it possible to use the firewire only to change the channels and still output the video through the composite? I ask because I am going here in a few minutes to grab a 3250 (or similarly firewire enabled box) to test with. Since I have firewire it is cheaper to do that than buy the IR stuff.

yes.

---

### Post by kameleon25 on 2008-07-17
They were out of the 3250's but had 4250's. I did not need HD for this test so I opted to just add my brother to the "authorized users" so he can go get a 3250 today. Hopefully they will have some today.

I also noticed this: [https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend](https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend) last night while digging through some other stuff. I am so glad they did that as I have an MVP and had tried unsucssfully to get it to work with my myhtbuntu box. So now I think my only issue will be my router doing the DHCP I will have to add a forward to my myth box.

---

### Post by majoridiot on 2008-07-17
> **kameleon25 said:**
> They were out of the 3250's but had 4250's. I did not need HD for this test so I opted to just add my brother to the "authorized users" so he can go get a 3250 today. Hopefully they will have some today.

I also noticed this: [https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend](https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend) last night while digging through some other stuff. I am so glad they did that as I have an MVP and had tried unsucssfully to get it to work with my myhtbuntu box. So now I think my only issue will be my router doing the DHCP I will have to add a forward to my myth box.

i helped another user get his mediamvp going, and it worked very well- and resulted in that wiki.  in 
fact, the setup that wiki describes was for routers handling the DHCP, so you shouldn't have problems.  
if you come up with anything new or helpful, please add to that wiki. :)

FYI- the mediamvp (with mvpmc firmware) does not currently like AC3 audio streams... so if you are
having audio issues, that is the first thing to check.

---

### Post by kameleon25 on 2008-07-17
I saw that you had done alot on it. I do thank you and I will add what I can when/if I find something useful. I have setup my mythbuntu box and will test the mediamvp when I get home if all goes well. I read where if you have a pvr-150 you are ok. I have a pvr-500 which is just 2 150's in a single card so I think I will be ok. Thanks for the heads up though. ;)

---

### Post by majoridiot on 2008-07-17
> **kameleon25 said:**
> I saw that you had done alot on it. I do thank you and I will add what I can when/if I find something useful. I have setup my mythbuntu box and will test the mediamvp when I get home if all goes well. I read where if you have a pvr-150 you are ok. I have a pvr-500 which is just 2 150's in a single card so I think I will be ok. Thanks for the heads up though. ;)

the pvr-xxx cards work very well... they record mpeg audio by default.  you should have very good 
luck using the mediamvp as a frontend for shows recorded with them.  the setup the wiki was developed
from used pvrs to record from stbs with channel changing handled by firewire- and worked very well, 
according to samo.  mythvideo works well too- as long as you avoid the aforementioned ac3 audio.

thanks for expanding on that wiki... there is a LOT you can do with it as a frontend for mythtv, but since
i didn't have hands-on access, none of that info was ever developed.  i look forward to you hopefully
filling in some of the blanks.  i don't think there are many people using them right now, but with better
info, that could change.

---

### Post by kameleon25 on 2008-07-17
They are great little boxes. The WAF is high as it brings the functionality of the myth box in a very small and almost unseen factor. My plans are to get another PVR-500 for my backend and have one or 2 more mvp's, one for each bedroom and maybe one in my office. Low power, very small form factor, but HIGH on the features. I like. lol

---

### Post by kameleon25 on 2008-07-18
Ok, update. When my brother goes to get the 3250 they don't carry that model. Supposedly the 4250 is the same but with HD. So I guess that means I can do HD now too. lol I will be testing it over the weekend and see how it goes.

---

### Post by Joshua on 2008-08-07
> **kameleon25 said:**
> They were out of the 3250's but had 4250's. I did not need HD for this test so I opted to just add my brother to the "authorized users" so he can go get a 3250 today. Hopefully they will have some today.

I just saw this.  Do you mean to say that 3250's are not HD?

3250 = Digtial SD?
4250 = Digital HD?

And you just want the 3250 for now?

If that's the case then I'm all fired up again about Comcast telling me that the 3250 is the only box they have with an active Firewire port.  I'm gonna have to call them back and get on my FCC complaint.

---

### Post by Joshua on 2008-08-07
For anyone that's still interested, I never heard back from Comcast.  I didn't really expect to, but I've been busy with other stuff lately anyway.  So I haven't even gone to get a 3250 to test stuff out.

But I did randomly get a call back from the FCC (took about 4 weeks after my original message).  I asked the guy how he interpreted the regulations, and he said that they should be able to activate the Firewire port on ANY box that they provide.

The relevant regulations are in CFR Title 47, Part 76, Section 640 (subsection b-4 on page 604) at [http://edocket.access.gpo.gov/cfr_2007/octqtr/pdf/47cfr76.640.pdf]("http://edocket.access.gpo.gov/cfr_2007/octqtr/pdf/47cfr76.640.pdf"):

> (4) Cable operators shall:
(i) Effective April 1, 2004, upon request
of a customer, replace any leased
high definition set-top box, which does
not include a functional IEEE 1394
interface, with one that includes a
functional IEEE 1394 interface or upgrade
the customer’s set-top box by
download or other means to ensure
that the IEEE 1394 interface is functional.
(ii) Effective July 1, 2005, include
both a DVI or HDMI interface and an
IEEE 1394 interface on all high definition
set-top boxes acquired by a cable
operator for distribution to customers.

So in section (i) they have to be able to upgrade my box or get me a new one, and in section (ii) any box they give me should already have it.

He also said that they are required to provide some sort of “pass-through” technology so that I can choose to watch either analog or digital with any box until 2012, but I couldn’t get a reference anywhere in the regulation and it sounded like he was speaking anecdotally.  He might have been mixing up what I was saying with the ability to pass analog broadcast channels through a digital converter box or through an analog cable box.

Anyway, I’m going to call Comcast one more time now and get started on my FCC complaint.

---

### Post by majoridiot on 2008-08-07
> **Joshua said:**
> I just saw this.  Do you mean to say that 3250's are not HD?

3250 = Digtial SD?
4250 = Digital HD?

And you just want the 3250 for now?

If that's the case then I'm all fired up again about Comcast telling me that the 3250 is the only box they have with an active Firewire port.  I'm gonna have to call them back and get on my FCC complaint.

as far as i know (and the google seems to agree), the 3250 is an HD/SD box.  i can't find a mention of an
SD-only 3250.

[http://www.nwi.net/PDF/Explore-3250HD.pdf](http://www.nwi.net/PDF/Explore-3250HD.pdf)

---

### Post by majoridiot on 2008-08-07
> **Joshua said:**
> For anyone that's still interested, I never heard back from Comcast.  I didn't really expect to, but I've been busy with other stuff lately anyway.  So I haven't even gone to get a 3250 to test stuff out.

But I did randomly get a call back from the FCC (took about 4 weeks after my original message).  I asked the guy how he interpreted the regulations, and he said that they should be able to activate the Firewire port on ANY box that they provide.

The relevant regulations are in CFR Title 47, Part 76, Section 640 (subsection b-4 on page 604) at [http://edocket.access.gpo.gov/cfr_2007/octqtr/pdf/47cfr76.640.pdf]("http://edocket.access.gpo.gov/cfr_2007/octqtr/pdf/47cfr76.640.pdf"):



So in section (i) they have to be able to upgrade my box or get me a new one, and in section (ii) any box they give me should already have it.

He also said that they are required to provide some sort of “pass-through” technology so that I can choose to watch either analog or digital with any box until 2012, but I couldn’t get a reference anywhere in the regulation and it sounded like he was speaking anecdotally.  He might have been mixing up what I was saying with the ability to pass analog broadcast channels through a digital converter box or through an analog cable box.

Anyway, I’m going to call Comcast one more time now and get started on my FCC complaint.

great info, joshua... thank you!

it's good that the FCC guy did manage to interpret the regs correctly.  i hope you got his name and
contact info in case you need it in the future?

i'm really surprised you are having such difficulty with comcast.  they are *generally* one of the
better cable providers when it comes to firewire and following the regs.  by any chance did
comcast recently take over your cable co?  that would explain their stalling/misinformation.

---

### Post by dannyboy79 on 2008-08-07
> **majoridiot said:**
> as far as i know (and the google seems to agree), the 3250 is an HD/SD box.  i can't find a mention of an
SD-only 3250.

[http://www.nwi.net/PDF/Explore-3250HD.pdf](http://www.nwi.net/PDF/Explore-3250HD.pdf)

he may have gotten an SA3250 not an SA3250HD.

see here: [http://www.cisco.com/en/US/products/ps8627/products_data_sheets_list.html](http://www.cisco.com/en/US/products/ps8627/products_data_sheets_list.html)

---

### Post by majoridiot on 2008-08-07
> **dannyboy79 said:**
> he may have gotten an SA3250 not an SA3250HD.

see here: [http://www.cisco.com/en/US/products/ps8627/products_data_sheets_list.html](http://www.cisco.com/en/US/products/ps8627/products_data_sheets_list.html)

that was a link i had bookmarked @ home... a couldn't seem to find it today.

thanks for clarifying that, dannyboy.  accurate info is everything.  joshua definitely needs to find out
which version his local comcast provides...

---

### Post by kameleon25 on 2008-08-07
I still have the 4250 sitting in my office waiting for me to get off my butt and hook it up. I have looked around (albeit not very heavily) for the firewire channel changing stuff for mythtv. Would someone be able to point me in the right direction to get this thing going?

---

### Post by kameleon25 on 2008-08-07
Also on a side note. I finally got in my second PVR-500 the other day. Newegg was out as was a few of my other primary picks. Ended up ordering off ebay and luckily got a new in box still shrink wrapped product. I need to find a time when I am home and the mythtv box isn't recording anything to install it. This is what will be taking the input from the SA4250 hopefully.

And majoridiot: I have yet to have plugged the mvp into the network to test the stuff we spoke about before. I hope to do that soon too. Too much to do and not enough time. lol

---

### Post by dannyboy79 on 2008-08-08
> **kameleon25 said:**
> I finally got in my second PVR-500 the other day. This is what will be taking the input from the SA4250 hopefully.

why are you referring to using firewire if your inputing from the 4250 to a PVR-500? Or do you only want to use firewire for channel changing? I couldn't get my 3250HD to work with my firewire channel changing so I ended up going the ir-blaster route and it works flawlessly!

---

### Post by kameleon25 on 2008-08-08
Yes, I planned on using the firewire to change the channels since I have that already on the myth box and I won't have to spend more on the IR option. Although I may have to opt to do that route anyways since I am not sure how much longer I will have Comcrap. I can get a better deal by switching to dish, I just don't agree with the 24 month contract. But that is neither here nor there.

The reason I don't want to mess with the video coming through the firewire is having to mess with the encryption. If I just output the composite to the pvr-500 then I won't have to mess with that. ;)

---

