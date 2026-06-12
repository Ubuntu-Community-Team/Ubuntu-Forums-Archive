---
title: "Help with new HTPC"
date: 2010-10-05
forum: Mythbuntu
---

### Post by wsume99 on 2010-10-05
[FONT=Calibri][SIZE=3]I’ve finally decided to make the jump and setup a dedicated HTPC and I’m in need of some advice. I’ve used ubuntu before (but not currently) and I’m running an unRAID server so I’m not a total linux noob but I’d say it’s safe to assume that I have zero linux skills. But I can read and follow instructions so I’m thinking I can make it work.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Here is what I want to do with my HTPC:[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]Play DVD and BluRay rips on HDTV streamed from media server (unRAID)[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]2.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]Record NTSC and QAM CATV using existing Hauppauge 2250 tuner[/SIZE][/FONT]
[FONT=Calibri][FONT=Calibri][SIZE=3]3.[/SIZE][/FONT] [/FONT][FONT=Calibri][SIZE=3]Play classic games (NES emulator)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I’ve been reading both the ubuntu and xbmc forums and right now I’m leaning towards a mythbuntu BE with a xbmc FE all housed in a single box and located on top of my media center cabinet that sits under my wall mounted LCD. This will be a new build and here is a list of the components I’m considering right now (priority placed on low noise and low power).[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]MB: [[COLOR=blue]ASUS AT3IONT-I Deluxe[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131635") (includes 90-watt DC power, 802.11n, Bluetooth, remote, & PCIeX16)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RAM: [[COLOR=blue]2x2GB G.SKILL DDR3 1333[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231318") (F3-10666CL7D-4GBECO)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Case: [[COLOR=blue]SILVERSTONE SG06-B[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811163151") (looking for alternatives)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]OS Disk: [[COLOR=blue]OCZ Agility 2 60GB SSD[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227542") (OCZSSD2-2AGTE60G)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Media Drive: [[COLOR=blue]WD Green 1.5TB[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136513") (WD15EARS)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Tuner: Hauppauge [[COLOR=blue]HVR-2250[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116037") (already owned)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Here are some things I’m looking for advice on:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]**_Motherboard selection_:** mini-ITX vs. micro-ATX. I’m leaning towards mini-ITX because I’m looking for a small footprint and it gives me the best low power and low noise performance. I chose the ASUS AT3IONT-I MB because it has the Atom CPU for low power but the ION GPU which, based on everything I’ve read here and over at xbmc forums, has enough power to display 1080p streams on my HDTV. I’ve considered a LGA 1156 mini-ITX board but not sure that the intel GPU is up to the task. If it isn’t and I need a discrete graphics card then my only expansion slot would be occupied and I won’t be able to utilize my existing Hauppauge tuner.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]**_Media Drive_:** I’m debating whether or not to have a media drive in my HTPC. I could record directly to my server but I just figured it would be easier to do it to a local disk. Removing the HDD would eliminate a source of heat and noise but would probably drive up my power costs since I’d have to wake the server to record to it. So I’d need two machines running to record a TV show.[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]**_Case_:** First priority – high WAF (wife approval factor). Looking for an alternative but really depends on what size MB I select. The Silverstone SG-06 is nice looking but comes with a PSU that I don’t need so that drives up the cost and I’d like something a little smaller. I looked at the [[COLOR=blue]Gigabyte GZ-SPIM51-P0B[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811233060") [/FONT][FONT=Calibri]case and it looks more like what I want but there is no expansion slot. My tuner is a half height card so I might be able to mod the case to add it but I’m not sure. Haven’t found any posts yet where someone used this case so it’s a risky option.[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]Any other comments welcome as I’m sure that it will be helpful.[/SIZE][/FONT]

---

### Post by elperrillo on 2010-10-05
Definitely go with Mythbuntu, I have tried then all, knoppmyth, mythdora, sageTV, etc. none of them come close. With Ubuntu you are getting the comfort of not having to look for drivers and mythTV you are getting the best DVR software. Mythbuntu has the best of both worlds. 

Follow this quick setup guide, this will get you up and running in the fastest time possible:

[http://geekyprojects.com/dvr-pvr/building-your-own-dvr-mythtv-quick-setup-guide/]("http://geekyprojects.com/dvr-pvr/building-your-own-dvr-mythtv-quick-setup-guide/")

Also, there is absolutely no need to build separate servers and clients. You can control Mythbuntu from another computer from anywhere in you house using NX and it will be as fast as if you were standing there in front of the server, follow this article to install NX on your MythTV box and on you Windows or Linux computer:

[http://geekyprojects.com/general/manage-mythtv-remotely-with-nx/]("http://geekyprojects.com/general/manage-mythtv-remotely-with-nx/")

---

### Post by LowSky on 2010-10-05
Hi welcome to the forums.


This [antec case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811129081") would be better if you wanted to use the tuner in the FE box, also has a built in power supply

Also look for an mITX MB with a Nivida 9300 chipset, [heres a few]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007627+600009028+600008073&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=280&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc="). It will give you more power, and if you want to use something like Boxee or Hulu Desktop more CPU power for those needs.

Personally I would put the tuner in the server if you can. My reasons:
1. Less parts, noise and heat in the ITX case.
2. The FE box can be off when not in use (thinking WAF). once scheduling is done on the fontend it gets written to the backend to process.
3. Server will only be awake when needed, just like before.


If the server cant run a PCIe card then I guess you back to making the mITX machine do everything, which is fine. Those green drives are really quiet and heat isn't too bad. But spend the $20 extra and get a 2TB drive. You will be amazed how much space 1 hour of HDTV takes up.


Lastly recodring NTSC with the 2250 might be a bit hard. The driver is still kinda experimental for that. But recording QAM is just fine, so long as you follow my tutorial 	;-)

[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

---

### Post by wsume99 on 2010-10-05
Thanks for the reply LowSky.  I've seen some of your other posts and they too have been helpful.

I'm looking at the Nvidia 9300 boards you suggested and I'll repost my revised h/w list later.  I was a concerned that the Atom would not be enough CPU for my needs so a full blown LGA775 might be better.  I guess trading a little power consumption for flexibility is worth it.

Also,WRT the post you linked concerning the Hauppauge 2250.  The post is from May 2010.  Has anything changed since then WRT NTSC recording and the 2250?  Your reply to my post said "it might be a bit hard".  Does that mean it is possible but will take some work or will my system be unstable?   The vast majority of my recording would be NTSC so if I can't get it to work then this could be a deal breaker for me and Mythbuntu.  Is this issue being worked or is NTSC support not a priority.  If NTSC support does not materialize for my tuner then I'd have two options, stay with windows 7 MCE or get a new tuner that has NTSC support in unbuntu.  Seeing as how I can do the former without spending any money that would probably be the option I'd choose.  I don't know if recording from my server is an option.  I do have several open PCIe slots I could use but I'm running unRAID on it now.  I suppose that there is some way to make it work but I don't have any clue where to begin.  I've read on the unRAID forums about setting up VMs on unRAID but as my original post indicated - I'm a linux noob so I would need some SERIOUS help with that.  I'll have to research that route a little more.

Bottom line is I want to get away from using my win 7 PC for anything besides photo editing.  My wife uses that box for her photography so I try to steer clear of it if you know what I mean.

---

### Post by LowSky on 2010-10-06
Just to point out if you have a copy of Win7 and it works, I will say use it if you don't mind DRM. The tuner completely works with Media Center 7 and the channel guide is free, where as with Mythtv you will need to purchase a license form schedulesdirect.org for $20 per year. $20*5=$100 which is the cost of an OEM copy of Win7

Can I ask why NTSC is so Important for you? ATSC/QAM is the new digital standard.
I want to make sure you are not getting terms confused

See this link for the support for analog recording. 
[http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490)

instructions for installing analog support are not too bad, much like digital
I can't really confirm them working yet as I don't have a need for it,  but the link above has people talking about it in full. hopefully you can get it working.

> **LowSky said:**
> The download and install instructions for analog support should look like this

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

---

### Post by Shompol on 2010-10-06
I went with full ATX, my box is huge, but because it is horizontal and good-looking, the WAF is OK with it. Most of the size is hidden from front view. What I get is lots of space to upgrade and tinkle with it. Don't forget that for gaming and 1080i in general you need a decent graphics card. Turned out my Nvidia is barely pulling it.

---

### Post by LowSky on 2010-10-06
I used to keep my media center in a full sized HTPC case but it was just too awkward and heavy. I can't suggest it.
I decided why use two PC's when I could run two X sessions from one machine. All it takes is a Nvidia video card with more than one output and a long video cable. Both session share the mouse and keyboard all I need to do is scroll over to the next monitor. Mind you I'm running some decent hardware. The way I see it I save money on electricity and shelf space.

---

### Post by wsume99 on 2010-10-06
> **LowSky said:**
> Can I ask why NTSC is so Important for you? ATSC/QAM is the new digital standard.
I want to make sure you are not getting terms confusedMy 2250 is currently installed in my primary desktop running win7. With MC7 I get about a dozen or so unencrypted QAM channels. The unencrypted channels are basically the OTA channels (ABC, CBS, NBC, FOX, PBS) that the cable provider is required by law to retransmit via unencrypted QAM. All the other cable channels come thru on the NTSC tuner. Since most of the shows I record are on cable stations I do most of my recording in NTSC. I don't like that but my only work around is to get a second STB and a HD-PVR. So I'd be spending $200 up front and $8/month for a single tuner. Not an attractive option for me. (Actually I've considered a Ceton cablecard quad-tuner but the price is a little too steep and the whole DRM mess is problematic).
 
 
> **LowSky said:**
>  
See this link for the support for analog recording. 
[[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=1567490[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1567490") 
I read that thread yesterday and the 31-page one that it originated from as well. So far I have not seen anyone report success with their setup.
 
 
> **LowSky said:**
>  
I used to keep my media center in a full sized HTPC case but it was just too awkward and heavy. I can't suggest it.
I decided why use two PC's when I could run two X sessions from one machine. All it takes is a Nvidia video card with more than one output and a long video cable. Both session share the mouse and keyboard all I need to do is scroll over to the next monitor. Mind you I'm running some decent hardware. The way I see it I save money on electricity and shelf space. 
Actually this is the opposite of what I'm trying to do. I currently watch ripped DVDs and recorded TV on my primary desktop with 24" monitor. Now I want to watch it on my 52" LCD in the living room. I decided that the best way to accomplish this was to build a standalone HTPC. Maybe that was a bad decision but I think that is what's best for me and my reason for posting here. If I build a standalone PC then I'll need a new OS which is where unbuntu comes in. If I have to use win7 to get NTSC support then I'd have to buy another license for my HTPC. Maybe I'll just have to build it and see if I can get NTSC working with the 2250 and mythtv.

---

### Post by wsume99 on 2010-10-08
I've been reading around and I'm wondering if I might be better off just downloading recorded shows off the net rather than recording them myself.  Looks like some people are using Sickbeard for this. I have no experience with it at all. Is this a good route for me to go?  Is there a better application to suit my needs?  Any advice is welcome.

---

### Post by LowSky on 2010-10-09
> **wsume99 said:**
> I've been reading around and I'm wondering if I might be better off just downloading recorded shows off the net rather than recording them myself.  Looks like some people are using Sickbeard for this. I have no experience with it at all. Is this a good route for me to go?  Is there a better application to suit my needs?  Any advice is welcome.

We cannot comment on this method. Downloading previously recorded programs may be a crime in your country.

I know this sounds confusing but recording TV yourself is seen as fair use.

---

### Post by wsume99 on 2010-10-09
Ok, well I guess I'll just have to wait until NTSC support is available for my tuner.

---

### Post by winewood on 2010-10-12
>  
Actually this is the opposite of what I'm trying to do. I currently watch ripped DVDs and recorded TV on my primary desktop with 24" monitor. Now I want to watch it on my 52" LCD in the living room. I decided that the best way to accomplish this was to build a standalone HTPC

 
I have found that for simplicity, I stream from my computer to my PS3.  It's $300-350, has a BlueRay disk player and works effortlessly using plain cat5 cable.  If you have Win7, the installed media player works to stream, or if you are lacking support and have 10 minutes to set it up, Tversity works as a streamer to your TV 
I only need my mythbackend for recording my shows this way and it makes needing a frontend for live tv only.  It is illegal to download most shows (from what I see), and why have to go out and find each show every day, sucking TONS of bandwidth and time, than with a few rules on the Mythbox, they all come to you at HIGHER resolution than what you can download reasonably on the net.
Off the air programs look AWESOME on the MythTV box, and with MythWeb, you can have a home webpage to download or stream the picture to your computer. All commercials are auto skipped!  In the long run, its cheaper and looks superior to paid for/ or stolen programming.

---

