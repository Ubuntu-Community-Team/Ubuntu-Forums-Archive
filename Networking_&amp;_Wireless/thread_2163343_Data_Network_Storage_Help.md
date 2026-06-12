---
title: "Data Network Storage Help"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by komrad3006 on 2013-07-18
I am wanting to setup a place to save files on my home network so i can access it anytime without having to have a certain computer on to get them off of,  My current router does not have a usb on the back to plug in a external hard drive.  so i am thinking, 

option one could i buy one of these [http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4983487&SRCCODE=WEBGOOPA&cm_mmc_o=mH4CjC7BBTkwCjCV1-CjCE&gclid=CPaB8rvzt7gCFUmk4AodmHsA3g](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4983487&SRCCODE=WEBGOOPA&cm_mmc_o=mH4CjC7BBTkwCjCV1-CjCE&gclid=CPaB8rvzt7gCFUmk4AodmHsA3g) ? one thing about those is i have no idea how to use it since you do not hook up a monitor to it from what i can see. 

option two, build a cheap computer and have it setup for a dedicated server, and if i do that would ubuntuu server be good to use or something like [FONT=verdana, geneva, helvetica][SIZE=2][COLOR=#000000]NetWare for an (NAS) machine. 

option three, just buy a router with a usb plugin on the back and buy a bigger external hard drive?

or if u all have some other options let me know to, thanks.
[/COLOR][/SIZE][/FONT]

---

### Post by theDaveTheRave on 2013-07-18
komrad3006,

all of the above options sound like a good solution to me.

the most flexible would be the 'cheap computer', you could probably go for something like a [rasperyPI]("http://www.raspberrypi.org/quick-start-guide"), available very [cheap, just £28]("https://export.farnell.com/jsp/raspi/orderPad.jsp?COM=raspi-group&country=GB") or one of the other minature footprint pc systems that are now available.

you could then plug in your external HDD via one of the USB ports

it could even double up as your media centre client, by plugging in you HDMI tv.

David

---

### Post by komrad3006 on 2013-07-18
I will have to look into te rasperyPI or something like it in some sort of fashon. I did find some for about $130+  but i may price a cheap computer build and put in some hard drive, i usualy use xubuntu but if i went the computer route, would ubuntu studio be my best bet? or some NAS OS like netware or similar.

---

### Post by theDaveTheRave on 2013-07-19
You could try for a networked HDD, this would be more 'mobil' (ie you could take the whole box on holiday with you to enjoy especially if you intend to use the drive for media storage.

for the general media centre...

I would start from whatever base you feel most happy with (xubuntu, lxde, kde, gnome or another), then add on those things required for the media centre functionality. Alternatively jump into a distro that is targeted to be a media centre (eg mythbuntu).

2 things to remember:
if you intend to use it to capture tv you need to ensure that your tv capture card is supported by linux.
a media centre 'client' is not the same as a media 'server' (although you can have a single box that behaves a both. Although if you are intending to get a 'cheap machine' it will probably only be good as a media centre 'client' as it will likely not have the capacity to stream media to multiple devices simultaneously.

quick example:

you may be able to stream 'music' to multiple devices (lets face it mp3 isn't exacly high bandwith these days). But if you have a media client in each room, and you wife wants to watch desperate houswives whilst she cooks diner, the lad is watching buffy, and the twins are streaming a karaoke game to the den with friends, and you want to watch Inception, and everyone is working on HD you may find that things get a little pixelated ! especially if your HDD access and network isn't up to it.


David

---

