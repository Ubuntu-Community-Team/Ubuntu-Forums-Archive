---
title: "Channel 5 (Five) now on Freesat"
date: 2008-11-19
forum: Mythbuntu
---

### Post by Modiford on 2008-11-19
Thanks to the folks on another thread I posted to I have managed to get my Hauppauge Nova-HD-S2 working in Mythbunto 8.10 and, lo-and-behold, I seem to have Channel 5 (or "Five").

I checked the Freesat website and sure enough the Five logo is listed on the available channels.  Finally, I can ditch the Sky box and get my fix of CSI on MythTV / Mythbuntu :-)

Regards,

Modiford.

---

### Post by Modiford on 2008-11-19
Quick reply to highlight the [Freesat website]("http://www.freesat.co.uk/index.php?page=whatson.Main") containing the latest line-up of channels.

The EIT program listings appear to be missing / not working though.

Regards,

Modiford.

---

### Post by Modiford on 2008-11-20
I may have been a bit hasty in saying the schedules weren't being received.  While looking into the Radio Times linked xmltv option the output said it was not enabled for any transports.  I then checked the channels and found many of the main stations like BBC and ITV had listings.  Others like Five and various music stations didn't.

The fun continues :-)

Kind regards,

Modiford.

---

### Post by drifting on 2008-11-21
Glad I am not the only one with listings missing, I get them via EIT, wished there was a list of channels that are known to have listings and those that don't! That way I would know it's not my installation.

Paul.

---

### Post by whych on 2008-11-21
It will all change again - only Five (region 2) is on at the moment.
This means there are now even fewer reasons to subscribe to sky. They have lost a lot of sport to Setanta and no longer have a monopoly - only a good thing.
You will need to rescan the satellite sometime soon because the channel listings will change again.
xmltv for Radio Times should list Five - you probably need to re-link the new listing to display it. (At least I have to with my dreambox running Linux)

---

### Post by drifting on 2008-11-22
Yes I agree about Sky, but to be honest I gave up on them a long while ago, wished I could find a difiniative list of the channels that do have listings. And I accpet your comment about xmltv, but never could get it to run right for me..

Paul.

---

### Post by Neon Dusk on 2008-11-22
> **drifting said:**
> ... wished I could find a difiniative list of the channels that do have listings ...

Paul.

I think all the offical Freesat channels (i.e. the ones listed on the Freesat website) should have the full EIT epg. The exception will be five and ITV HD - I expect the EIT epg for five will be there soon.

---

### Post by the goat boy on 2008-11-24
hello there

How did you manage to get your boxes running with the EPG?

If I scan the channels for EPG data with the EIT scan, it comes back blank.

I am currently using the xml radio times link, but if I try to record, I keep getting errors back.

does anyone know of a good guide for freesat receiving on mythbuntu??

---

### Post by Modiford on 2008-11-24
Hello the goat boy, and other fellow posters,

I enabled the EIT option (I am at work, so cannot recall the exact setting name) and the EPG data eventually populated through.  If you have a Sky Digibox you'll know how long the 'Searching for channel listings' can take to complete from powering one on.

It's a case of having patience!  Channel 5 is new to Freesat so perhaps the Freesat-ifying of the EPG format is being done behind the scenes.

Fortunately all I need to know is 9.00pm on Tuesday to get my CSI on Five fix - EPG or no EPG!

Regards,

Modiford.

---

### Post by Neon Dusk on 2008-11-24
Check checked this and the full 7 day EIT EPG is now there for five.

---

### Post by the goat boy on 2008-11-25
> **Modiford said:**
> Hello the goat boy, and other fellow posters,

I enabled the EIT option (I am at work, so cannot recall the exact setting name) and the EPG data eventually populated through.  If you have a Sky Digibox you'll know how long the 'Searching for channel listings' can take to complete from powering one on.

It's a case of having patience!  Channel 5 is new to Freesat so perhaps the Freesat-ifying of the EPG format is being done behind the scenes.

Fortunately all I need to know is 9.00pm on Tuesday to get my CSI on Five fix - EPG or no EPG!

Regards,

Modiford.

thanks for the help. I tried this method last night, and some channels did populate, but the BBC channels and five for instance did not.

How long have you left it running before the EPG populates?

And does it make a difference that I have changed the channel number of the channel? (i.e. BBC 1 is now 101 for instance)

cheers

TGB

---

### Post by drifting on 2008-11-25
> **the goat boy said:**
> thanks for the help. I tried this method last night, and some channels did populate, but the BBC channels and five for instance did not.

How long have you left it running before the EPG populates?

And does it make a difference that I have changed the channel number of the channel? (i.e. BBC 1 is now 101 for instance)

cheers

TGB

There was an option I checked somewhere in the tuner setup part, that mentioned allowing EPG data whilst recording, not sure of the implications of that, but now I have listings for 5. Do any of you get listings for Film24 ? As someone previous said about sky channels, yet I get listings for Movies4men?

Paul.

---

### Post by Neon Dusk on 2008-11-25
Film24? Do you mean Film4?

Film4, Film4+1, movies4men, movies4men2 are offical Freesat channels and have full eit listings (movies4men+1 doesn't have listing as it's not part of Freesat)

---

### Post by the goat boy on 2008-11-26
thanks to all the above posters. 

after playing with mythbuntu last night, i got my epg. still no channel 5 tho

but all other channels seemed to have worked

---

### Post by the goat boy on 2008-11-27
Well I thought it had worked.

I set up two timer recordings last night.

Heroes on BBC 2 at 9.00 and at 10.00 on BBC HD

neither of the programs recorded.

I just had two copies of the national lottery recorded.

Does anyone else get this problem?

am i doing something wrong?

---

### Post by Modiford on 2008-11-27
Hello Fellow Forum Folks,

I checked this morning before I left and Channel 5 / Five still has no EPG, Scuzz does but not their +1 channel, the Zone channels have EPG except for Zone Horror.  Seems a bit hit'n'miss considering someone else here claims to have Five EPG.

For recording scheduled programs the goat boy, I have had no problems.  If anything it records too much; I asked for Spooks to be recorded and got Spooks Code 9 into the bargain.

There used to be a command called 'mythtv-status' on the previous version of Mythbuntu that revealed upcoming recordings but it appears absent from the current version.  Depending on the version you're running the goat boy perhaps you can set some programs to record and call up the command and see what's what there.

Regards,

Modiford.

---

### Post by the goat boy on 2008-11-27
I am running the latest version

I will see if i can try this command when i get home

---

### Post by Neon Dusk on 2008-11-27
@Modiford
Scuzz+1 isn't on the offical Freesat epg (A full Freesat epg can be found [here](http://www.digitalspy.co.uk/satellite/freesatepg/)). 

Zone Horror seems fine here. Maybe you need to rescan your transports to pickup the missing listing?

---

### Post by Modiford on 2008-12-09
Hello Neon Dusk,

I wonder whether you would be willing to tell me know the entries you have for Channel 5 / Five in your Mythconverg database?  I'll compare it to my 'scanned' Five and change it as appropirate.  Still no EPG on the one my Myth box scanned.

I'd rather not rescan all transports having manually re-indexed all the channels in MySQL and removed all the other random channels (using the RSI inducing "update x set y = #### where z = '.....' " a few dozen times).

Kind regards,

[Modiford.]("http://www.freebsdwiki.net/index.php/User:DrModiford")

---

### Post by Neon Dusk on 2008-12-09
Not sure how the formatting will look but here goes :-
```

channel table
chanid 	channum 	freqid 	sourceid 	callsign 	name 	icon 	finetune 	videofilters 	xmltvid 	recpriority 	contrast 	brightness 	colour 	hue 	tvformat 	commfree 	visible 	outputfilters 	useonairguide 	mplexid 	serviceid 	atscsrcid 	tmoffset 	atsc_major_chan 	atsc_minor_chan 	last_record 	default_authority 	commmethod	
7335 	1105 	  	1 	Five 	Five 	  	0 	  	  	0 	32768 	32768 	32768 	32768 	Default 	0 	1 	  	1 	285 	6335 	NULL 	0 	0 	0 	0000-00-00 00:00:00 	  	-1

dtv_multiplex table
SELECT *
FROM `dtv_multiplex`
WHERE `mplexid` =285

mplexid 	sourceid 	transportid 	networkid 	frequency 	inversion 	symbolrate 	fec 	polarity 	modulation 	bandwidth 	lp_code_rate 	transmission_mode 	guard_interval 	visible 	constellation 	hierarchy 	hp_code_rate 	sistandard 	serviceversion 	updatetimestamp
	285 	1 	2045 	2 	10773250 	a 	22000000 	5/6 	h 	qpsk 	NULL 	NULL 	NULL 	NULL 	0 	NULL 	NULL 	NULL 	dvb 	14 	2008-11-19 19:57:09
	
program table
SELECT *
FROM `program`
WHERE `chanid` =7335

has data up to 16-12-2008

```

The only thing that I can see is the useonairguide flag in the channel table. Could it be that when you originally added the channel the epg wasn't broadcasting so useonairguide got set to 0?

---

### Post by ianhaycox on 2008-12-10
I had the same problem with the EPG on Five.

Changing useonairguide to 1 for Five fixed it for me. I tuned the frontend into Five and with an hour I had a weeks worth of EPG data.

Thanks.

---

### Post by Modiford on 2008-12-24
Hello Neon Dusk,

Sorry for the delay in my reply, I am between rentals at the moment (I physically cannot move another box!).  You were right on the money with the Use On-Air Guide setting - now Channel 5 / Five is showing listings :-)

As another question does anyone know when the Nova-HD-S2 and other cards requiring the custom kernel compilation method will be supported "out of the box" using a clean installation of Mythbuntu?  I've searched around but found very little.

I know the PVR-250 (also by Hauppauge) took some time to be supported and works well now in the current releases so I'm willing to wait.  At least I can save up for a few more HD tuners and a quad-LNB and make a full MythTV home setup :-)

Many thanks,

Modiford.

---

### Post by Neon Dusk on 2008-12-25
Good to know it's working

I think the most up to date info is found [here](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000) acording to that page a driver is expected in the kernel version 2.6.28.

---

### Post by Modiford on 2008-12-25
> **Neon Dusk said:**
> Good to know it's working

I think the most up to date info is found [here](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000) acording to that page a driver is expected in the kernel version 2.6.28.

Once again many thanks Neon Dusk - you are such an Oracle of all knowledge!

I had a moment of feeling all n00b like just then realising I have spent farrr too long in the FreeBSD world to know what kernel version the Linux world are up to now.

Taking your reference to 2.6.28 I found a website listing all the features, and in particular, the classic [Video4Linux]("http://www.heise-online.co.uk/news/Kernel-Log-What-s-coming-in-2-6-28-Part-8-Video4Linux-DVB-Wireless-USB-hardware-monitoring-and-inp--/112278") [link] subsystem.

Listed part-way down the page is "cx88: Add support for the Hauppauge HVR4000 and HVR4000-LITE (S2) boards" thanks to "...support for the cx24116, si21xx, and stv0288 DVB-S2 chips; the cx88 and dw2102 drivers were improved to include DVB-S2 support."

Further searching (keeping an educated guess that Mythbuntu versions mirror the underlying Ubuntu releases) suggests that [Ubuntu 9.04]("http://www.ubuntu.com/testing/jaunty/alpha2") [link], and in what seems to be a tradition is code named "Jaunty Jackalope", is the one to look out for.

Again, I'm a FreeBSD guy so correct me if I am wrong with any of this!  (I'm sure by now this thread is also way off original topic).

Merry Christmas and a Happy New year to all,

Modiford.
Now at One Cup level :-)

---

### Post by Modiford on 2009-01-11
Hello All,

Over the weekend I have been playing with the current Alpha 2 release of Mythbuntu 9.04 using the Live CD option - and while not wanting to speak too soon, I think it's good news to all Hauppauge Nova HD S2 (sometimes called the HVR4000 Lite) owners!

My experience in getting the card to work involved the following (while in the Live CD environment):

o Install the 'unzip' utility using apt-get;
o Fetch the original drivers for Windows from a website;
o Extract the firmware file (using unzip);
o Create the firmware file using 'dd';
o Copy it to the firmware location on the system.

Then I used VLC Player to open the DVB device with some test frequencies (I think I ended up using the default ones which apepar to be BBC 1, UK) - and got glorious digital TV and sound!

I will be assembling a new system to install Mythbuntu into (including RAID 0 so I can have better drive performance - playback-while-recording is soo painful on the current box).  Once done I will post back a full step-by-step write-up of what I had to do to get the Hauppauge Nova HD S2 working.

Kind regards,

Modiford.

---

