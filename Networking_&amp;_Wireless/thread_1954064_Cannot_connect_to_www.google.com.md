---
title: "Cannot connect to www.google.com"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by Hotshot5000 on 2012-03-16
I had Ubuntu 11.10 and in the last few weeks I experienced an obscure problem: after I had the computer running for a few days I could no longer connect to google.com or anything related to google. All sites worked with all browsers (Firefox, chrome, opera) except google. It remained in the connecting phase for a few minutes and either timed out or finally connected with this huge delay. 

Even if I entered other sites such as this one, if it had anything to do with google such adsense or gstatic or whatever with g in it, that site took a long time to load waiting in connecting to gstatic.com . Anything google related took minutes to work, but everything else worked instantly!

I tried rebooting or using other machine(with windows on it) and this worked, so it's not network related. But after a few days it started not working again... So I upgraded to the Precise Pangolin beta hoping this behavior would go away. It didn't! After a few days I get the same behavior as in 11.10.

What am I supposed to do? Reboot every other day? I have 3 servers: an apache web server, a mysql server, and my server written in java listening to port 30003. Could it be related to this? Other than this I am running nautilus, two terminals, gimp, pidgin and skype, gedit, orage calendar, but I don't think these should have anything to do with my browsing...

---

### Post by grahammechanical on 2012-03-16
As you have noted, this issue is not specifically related to 12.04 Precise. It was happening with 11.10 as well. Not only that it is a problem specific to google related sites.

This tells me that the problem is not coming from the operating system but to some configuration setting.

It is my guess that you will get more help from the forum section set aside for Networking problems.

An upgrade to a later version does not remove or replace any of the user settings that are in the Home folder. This is useful but it does not solve problems caused by configuration conflicts. A new install with a format of the partition starts everything off afresh.

I am not saying that is the only solution but if you find that solving this issue is hard work and time consuming you might want to consider the new install or re-install option.

You could create a dual boot with 12.04 Beta and then try to set things up as you would like your OS to be. This I think is a good thing to do before going from one release of Ubuntu to another. In your case it might help you spot what it is that is causing this problem.

Regards.

---

### Post by Hotshot5000 on 2012-03-16
I agree that this is a configuration file issue. But I haven't changed anything. I had the computer up and running for about 4 months and then I restarted it. I cannot be sure when the behavior started showing but for those 4 months there definitely were no problems.

---

### Post by Hotshot5000 on 2012-03-16
I had Ubuntu 11.10 and in the last few weeks I experienced an obscure  problem: after I had the computer running for a few days I could no  longer connect to google.com or anything related to google. All sites  worked with all browsers (Firefox, chrome, opera) except google. It  remained in the connecting phase for a few minutes and either timed out  or finally connected with this huge delay. 

Even if I entered other sites such as this one, if that site had anything to do  with google such adsense or gstatic or any google component in it, that site  took a long time to load waiting in connecting to gstatic.com .  Anything google related took minutes to work, but everything else worked  instantly!

I tried rebooting or using other machine(with windows on it) and this  worked, so it's not network related. But after a few days it started not  working again... So I upgraded to the Precise Pangolin beta hoping this  behavior would go away. It didn't! After a few days I get the same  behavior as in 11.10.

What am I supposed to do? Reboot every other day? I have 3 servers: an  apache web server, a mysql server, and my server written in java  listening to port 30003. Could it be related to this? Other than this I  am running nautilus, two terminals, gimp, pidgin and skype, gedit, orage  calendar, but I don't think these should have anything to do with my  browsing...

I had the computer running for 4 months and I hadn't had this behavior. Also I didn't poke in any configuration files, but after a restart (all those updated piled up) this started happening. I cannot know which update did this...

---

### Post by matt_symes on 2012-03-16
Hi

Create a new user. Log in as that user and check the google sites you are having problems with.

Do you still have the same problems ? If not the problem is with your user settings.

If yes then the problem is elsewhere.

Kind regards

---

### Post by Hotshot5000 on 2012-03-16
Yeah. The thing is this error doesn't happen immediately, it takes a couple of days to show. But I'll try and see if I can get it again...

---

### Post by matt_symes on 2012-03-16
Hi

What dns server are you using ? Have you cleaned all your web caches ?

What router are you using ?

Do you get the same problem if you use wget to get the page ?

Have you tried using a google IP address instead of [www.google.com](www.google.com) to get the page.

These are all things i would be looking at to try to isolate the problem.

Kind regards

---

### Post by Hotshot5000 on 2012-03-20
So I have the problem right now. I cleaned the firefox cache, I tried the ip instead of the address of [http://www.google.com/](http://www.google.com/)... nothing, I tried wget and I get:

--2012-03-20 15:56:36--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com]("http://www.google.com") ([www.google.com]("http://www.google.com"))... 74.125.232.209, 74.125.232.210, 74.125.232.211, ...
Connecting to [www.google.com]("http://www.google.com") ([www.google.com)|74.125.232.209|:80]("http://www.google.com%29%7C74.125.232.209%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.ro/](http://www.google.ro/) [following]
--2012-03-20 15:57:07--  [http://www.google.ro/](http://www.google.ro/)
Resolving [www.google.ro]("http://www.google.ro") ([www.google.ro]("http://www.google.ro"))... 74.125.232.248, 74.125.232.247
Connecting to [www.google.ro]("http://www.google.ro") ([www.google.ro)|74.125.232.248|:80]("http://www.google.ro%29%7C74.125.232.248%7C:80")... failed: Connection timed out.
Connecting to [www.google.ro]("http://www.google.ro") ([www.google.ro)|74.125.232.247|:80]("http://www.google.ro%29%7C74.125.232.247%7C:80")... failed: Connection timed out.


It automatically redirects me to google.ro (I am from romania). All other sites and addresses seem to work except anything related to google. On another computer (with windows 7) connected to the same router everything works OK. It connects to google instantaneously.

ping works but wget or lynx or anything browser related doesn't.

When you said to clean cache what exactly did you mean? tools->clear recent history? I did that still nothing

---

### Post by matt_symes on 2012-03-20
Hi

> ping works but wget or lynx or anything browser related doesn't
That's odd.

> The thing is this error doesn't happen immediately, it takes a couple of days to show.

Does a reboot of your PC rectify the problem ?

Kind regards

---

### Post by Hotshot5000 on 2012-03-20
Yes a reboot solves the problem. But I don't think it's normal to have to reboot every couple of days...

---

### Post by matt_symes on 2012-03-20
Hi

> **Hotshot5000 said:**
> Yes a reboot solves the problem. But I don't think it's normal to have to reboot every couple of days...

I agree. I'm not sure what would cause this.

You have tried stopping and restarting everything network related ?

```
sudo service network-manager stop
```

```
sudo service network-manager start
```

```
sudo /etc/init.d/networking restart
```

Kind regards

---

### Post by Hotshot5000 on 2012-03-20
Tried all those three commands in that order. Still not working...

---

### Post by matt_symes on 2012-03-20
Hi

> **Hotshot5000 said:**
> Tried all those three commands in that order. Still not working...

I have to say, i'm a bit stumped by this one :confused: It's not a problem i have ever had.

Do you have any unusual net software installed on your PC ? Are you going through a proxy, tor ?

Try this IP address in your browser.

```
matthew@matthew-Aspire-7540:~$ nslookup www.google.co.uk
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
www.google.co.uk        canonical name = www-cctld.l.google.com.
Name:   www-cctld.l.google.com
Address: **173.194.78.94**

matthew@matthew-Aspire-7540:~$ 
```

Anybody else with any ideas or come across this one ?

Kind regards

---

### Post by Hotshot5000 on 2012-03-20
Doesn't work. It times out.

As about unusual net software I have an apache server, a ftp server, a mysql database and a java server listening on 30003 (it's killed now though so I don't think it should affect the system).

I am listening on following ports:

21/tcp   open  ftp
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql
3689/tcp open  rendezvous


Any ideas such as what configuration files to look into and maybe post here?

---

### Post by matt_symes on 2012-03-20
Hi

You do see anything interesting if you run  traceroute on it ?

```
sudo apt-get install traceroute
```

```
traceroute -p 80 www.google.ro
```

Kind regards

---

### Post by Hotshot5000 on 2012-03-20
No trace..just stars up to the 30 level. But then I tried a site that works like [www.canonical.com](www.canonical.com) and it also doesn't trace anything

---

### Post by matt_symes on 2012-03-20
Hi

I'm really stumped. At least a reboot is a work around. I will continue to ponder for you but...

Anybody else have any ideas ? 

Kind regards

---

### Post by Hotshot5000 on 2012-04-07
I have a very strange problem. After keeping the system on for about 2 days I can no longer connect to google.com or any other google service.

I tried connecting to the site with firefox chrome opera wget and lynx and all have the same behavior: after a couple of days it takes about 5 minutes to reach the site and retrieve the page. I tried using the ip directly still the same behavior. Absolutely any other site works and after a computer restart google works again. Any other computer on the network can connect to google while this one exhibits the weird behavior.

I have Ubuntu installed for more than a year and this bahavior started happening in the last month. So I tried reinstalling Ubuntu 11.10 (I had it updated from 11.04 which was updated from 10.10) and deleted most of the folders beginning with . from my home partition (I left those from netbeans, eclipse, skype and purple) hoping that it was a configuration file issue. After reinstalling and a couple of days still get this problem. I had the 32 bit version and now have the 64 version and whatever I do I still cannot leave the computer without a restart every 2 days!!!

Any ideas on what can I possibly do more? Or what conf files to look into?

I will also mention that I have multiple ntfs partitions with both windows xp and 7 installed if this could be of any help.

I have installed both kde and xfce beside gnome and Unity and I am using the gnome 3 fallback mode.

---

### Post by Ms. Daisy on 2012-04-09
What exactly do you see when you try and fail to connect to [www.google.com?]("http://www.google.com?") What errors do you get? 

Can you ping the router when you can't connect to google? 

Post the output of 
```
ifconfig
```

---

### Post by tehchibipanda on 2012-04-09
You said you still have windows on the computer, right? Or did I misread that post...if I misread, sorry. If you have windows and ubuntu on a dual boot system, do google and its services work fine on the windows partition?

---

### Post by mojorising on 2012-04-09
Ha. Pretty interesting problem! For us to help, it is very important to know exactly what happens when you can't fetch the site. Does it time out? Do you get any error messages? If so, what are the errors?

ping should definitely be the first quick check. Do you get any replies? You should as Google does respond to ICMP echo requests. If so, what's the round trip time on them (time=)? 

Try using netcat to see what things look like to a web browser when you try to fetch the page:

mike@hostname:$ nc [www.google.ca](www.google.ca) 80

Then type:
```

GET www.google.ca HTTP/1.1

```
Then press Enter twice. 

What's the output of that? It should be something like:
```

HTTP/1.1 200 OK
Date: Mon, 09 Apr 2012 06:36:22 GMT
Expires: -1
Cache-Control: private, max-age=0
Content-Type: text/html; charset=ISO-8859-1
Set-Cookie: PREF=ID=40e4d089b3df3d3d:FF=0:TM=1333953382:LM=1333953382:S=7QGhc8tMMOdW-m4I; expires=Wed, 09-Apr-2014 06:36:22 GMT; path=/; domain=.google.ca
Set-Cookie: NID=58=ASFZ8Pter_E2JM8UULFW5i70ydHH3vAmjj-7S5AF0oait_XQkc_zMX-seiTSfM-2NEq0KJu6mk1LnEjgwssCirMX1_k9BgxnQjfwf7bbqIdI5uKC8mwxeL6BxFwaAkU-; expires=Tue, 09-Oct-2012 06:36:22 GMT; path=/; domain=.google.ca; HttpOnly
P3P: CP="This is not a P3P policy! See http://www.google.com/support/accounts/bin/answer.py?hl=en&answer=151657 for more info."
Server: gws
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
Transfer-Encoding: chunked

1000
<!doctype html><html itemscope itemtype="http://schema.org/WebPage"><head><meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"><meta itemprop="image" content="/images/google_favicon_128.png"><title>Google</title><script>window.google={kEI:"ZoOCT8PcEMbXiAKYqsj9Ag",getEI:function(a){var b;while(a&&!(a.getAttribute&&(b=a.getAttribute("eid"))))a=a.parentNode;return b||google.kEI},https:function(){return window.location.protocol=="https:"},kEXPI:"30316,34635,34956,36683,36888,36934,37344,37359,37501,37517,37573,37646,37682,37858,38112,38159",kCSI:{e:"30316,34635,34956,36683,36888,36934,37344,37359,37501,37517,37573,37646,37682,37858,38112,38159",ei:"ZoOCT8PcEMbXiAKYqsj9Ag"},authuser:0,
ml:function(){},kHL:"en",time:function(){return(new Date).getTime()},log:function(a,b,c,e){var d=new Image,h=google,i=h.lc,f=h.li,j="";d.onerror=(d.onload=(d.onabort=function(){delete i[f]}));i[f]=d;if(!c&&b.search("&ei=")==-1)j="&ei="+google.getEI(e);var g=c||"/gen_204?atyp=i&ct="+a+"&cad="+b+j+"&zx="+google.time();
var k=/^http:/i;if(k.test(g)&&google.https()){google.ml(new Error("GLMM"),false,{src:g});delete i[f];return}d.src=g;h.li=f+1},lc:[],li:0,Toolbelt:{},y:{},x:function(a,b){google.y[a.id]=[a,b];return false}};

```

You can also try observing your connection attempts with a packet sniffer like Wireshark but that's a bit advanced (not too bad though).

I'm wondering if the problem might be on your router, even though the other PCs on your network don't have the problem (it's possible). Have you tried plugging straight into your cable/DSL modem? 


Good luck. I haven't been on the forums much lately but I'll try to remember to come back and see how it went. 


Mike

---

### Post by dontquoteme on 2012-04-09
The good news is that if you can connect to other sites that rules out your Linux pc, routers, and configuration - everything is fine with your setup.

The interesting news is that many others have experienced this issue... on Windows pcs as well as Ubuntu - over the past 3 years - and on a global basis.

[https://getsatisfaction.com/google/topics/_google_com_unable_to_connect](https://getsatisfaction.com/google/topics/_google_com_unable_to_connect)

very strange... i tried opening 209.85.171.100 in firefox, and it worked! It opened up the google page! When i type in [www.google.com]("http://www.google.com/") however, it wont work. I still cant use the search engine though, when i try to search it can not connect again. 

Original error:
I cannot connect to google.com or any other pages starting with  google.com/ &#305;nclud&#305;ng gmail.com (mail.google.com). (simple Internet  Explorer cannot display this page error)However I can access to  google.co.uk, google.be etc country sites, can perform search etc.I can  also connect to maps.google.com, news.google.com, groups.google.com  finance.google.com but nothing like google.com/support or  google.com/options or /sites, /reader /calender. (I am being transferred  to [http://www.google.com/calendar/render...]("http://www.google.com/calendar/render?hl=en&tab=ec") or [http://mail.google.com/mail/?hl=en&ta...]("http://mail.google.com/mail/?hl=en&tab=em")  which does not work.) 
my company laptop also stopped connecting gmail  from home. I am in Belgium, using XP and IE7 and I can connect to every  other site except for google.com, also to skype and live messenger. Any  suggestions on how to fix this?

So google.co.uk might work... and the google country sites, but google.com has the problem.


A workaround will be to use [www.startpage.com]("http://www.startpage.com") instead of google.
Startpage acts as a proxy - it will go to google, get the results but remove your IP so that Google never sees you.  I would recommend you switch all pcs to using startpage.com as the search engine... please don't use Google directly as they record your IP and read your email to sell to advertisers.

---

### Post by praseodym on 2012-04-09
Add the google nameservers 8.8.8.8 and 8.8.4.4 in the NM applet. Do you use a firewall? Please show

> lsmod

---

### Post by Hotshot5000 on 2012-04-09
Ms. Daisy: I can ping the router, I can restart it and change my ip and still connect to any other site than google.com (or google.ro since I am in Romania).

This is the result of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:33:59:47:6b  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fe59:476b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:959723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:911019668 (911.0 MB)  TX bytes:224931049 (224.9 MB)
          Interrupt:44 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2616574 (2.6 MB)  TX bytes:2616574 (2.6 MB)


[tehchibipanda]("http://ubuntuforums.org/member.php?u=859394"): It works just fine from other computers on the network or from this one if I restart it (either on windows or ubuntu). But I don't like restarting the computer every couple of days...

[mojorising]("http://ubuntuforums.org/member.php?u=1658"): ping answers in about 12-13 ms for google.com. nc doesn't work. I used google.com or google.ro or even google.ca they don't do anything I just wait for the response forever.

This is what I get from GET:
GET [www.google.com]("http://www.google.com") HTTP/1.1
Can't connect to [www.google.com:80]("http://www.google.com:80") (timeout)

LWP::Protocol::http::Socket: connect: timeout at /usr/share/perl5/LWP/Protocol/http.pm line 51.

<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en-US" lang="en-US">
<head>
<title>Topic Related Searching at HTTP.COM.</title>
<meta  name="description" content="Hypertext Transfer Protocol - Topic Related Searching (TRS)" />
<meta  name="keywords" content="http, hypertext, hypertext transfer protocol, topic related searching, trs, http.com, sponsored search results" />
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
<frameset rows="*,0" frameborder="NO" border="0" framespacing="0">
  <frame name="mainFrame" src="http://domains.googlesyndication.com/apps/domainpark/domainpark.cgi?cid=ca-dp-og03&s=HTTP.com">
</frameset>
<noframes>
<body bgcolor="#FFFFFF">
Please visit <a href="http://domains.googlesyndication.com/apps/domainpark/domainpark.cgi?cid=ca-dp-og03&s=HTTP.com">this link</a> since your browser does not support frames.
</body>
</noframes>
</html>


[dontquoteme]("http://ubuntuforums.org/member.php?u=1604311"): But if I restart the computer it works again. If I get ifconfig eth0 down and up I still get the problem. Startpage works! But this still doesn't solve my problem. What the hell is wrong with ubuntu? It used to work.

[praseodym]("http://ubuntuforums.org/member.php?u=1411497"): Adding those nameservers in /etc/resolv.conf didn't work. This is what I get from lsmod and no I don't have any firewall installed except the standard ufw but it isn't active

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
vesafb                 13809  1 
snd_hda_codec_realtek   330815  1 
snd_hda_intel          33390  4 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96714  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwl3945                83430  0 
snd_timer              29991  2 snd_pcm,snd_seq
iwl_legacy             83487  1 iwl3945
mac80211              462046  2 iwl3945,iwl_legacy
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17083  1 videodev
joydev                 17693  0 
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  3 iwl3945,iwl_legacy,mac80211
fglrx                2928969  316 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
r592                   18144  0 
video                  19412  0 
memstick               16569  1 r592
psmouse                73882  0 
nand_ecc               13230  1 nand
serio_raw              13166  0 
mtd                    33181  2 sm_common,nand
coretemp               13420  0 
sparse_keymap          13890  0 
toshiba_bluetooth      12807  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
r8169                  52788  0 



It seems like this isn't a google problem but an ubuntu one. I  completely reinstalled my system even formatted the home partition and  after 2 days of reinstalling I still get the problem!! This has to be an  ubuntu issue. Also connecting to youtube doesn't work (which is also owned by google). So the startpage solution still isn't complete.
Also just to make myself clear. It does connect after around 5 minutes. It's not that it doesn't connect. It does. Just extremely hard and sometimes I get a timeout if it takes too long. So instead of looking at a video on youtube and then clicking another video and have it start I wait for 5 minutes before it loads the next page.

---

### Post by Ms. Daisy on 2012-04-09
> **Hotshot5000 said:**
>  [praseodym]("http://ubuntuforums.org/member.php?u=1411497"): Adding those nameservers in /etc/resolv.conf didn't work. This is what I get from lsmod and no I don't have any firewall installed except the standard ufw but it isn't active 
If you added it to /etc/resolv.conf, then it won't be persistent.  That file is overwritten by network manager every 900 seconds and at every system startup.

If you add them through the GUI they will remain permanent (I haven't found where network manager saves the changes so I don't know how to do it through terminal).  

I am leaning towards a DNS problem here.  When you have the connection problem, try to ping [www.google.com](www.google.com) and then try to ping 8.8.8.8

---

### Post by Hotshot5000 on 2012-04-09
Both google and 8.8.8.8 answer immediately to ping (I am having the issue right now), but still cannot connect using any browser. I tried using automatic dhcp adresses only and added 8.8.8.8 and it still doesn't work. I mean everything works except google.com. It remains in connecting to google.com in firefox and sending request in chromium. Ok total insanity. I open VirtualBox and start an android x86 instance and from there google works. But from Ubuntu it just doesn't work!!!

---

### Post by dontquoteme on 2012-04-09
Prehaps you can use the /etc/hosts to your advantage.
1.Ping Google from one of your other machines to get the local IP for Google.ro.

2. Edit your /etc/hosts file to include the IP for the Romanian server in the local hosts file.

HOW to guide for editing hosts file:
[http://jaxov.com/2009/09/how-to-block-websites-in-ubuntu-linux/](http://jaxov.com/2009/09/how-to-block-websites-in-ubuntu-linux/)

Your pc should default to the local hosts file before checking with DNS - so for *.google.com you won't use  DNS on this pc.

3. A range of Google's name servers include:
2.) [http://74.125.225.84]("http://74.125.225.84/")
3.) [http://74.125.225.82]("http://74.125.225.82/")
4.) [http://74.125.225.80]("http://74.125.225.80/")
5.) [http://74.125.225.83]("http://74.125.225.83/")
6.) [http://74.125.225.81]("http://74.125.225.81/")

Hope that helps fix the initial problem.

---

### Post by Hotshot5000 on 2012-04-09
I'll update you on what I found out. I used wireshark and tried a wget to 74.125.232.244 and what I see there is that I keep getting TCP previous segment lost. And after I get these every like 3-5 seconds it redirects to other 74.125.232.* google servers (like 74.125.232.229, 230 etc) and I keep getting those previous segment lost messages on every server it tries. And after a looong time I finally get the file.

---

### Post by dontquoteme on 2012-04-10
> **Hotshot5000 said:**
>  I keep getting TCP previous segment lost. And after I get these every like 3-5 seconds it.

Found an interesting solution that might be worth doublechecking - as this fault varies website by website (it's a TCP setting) and triggers the error you're getting in Wireshark:

[http://www.linuxquestions.org/questions/linux-networking-3/bizarre-tcp-connectivity-issues-from-certain-clients-totally-mystified-771804/](http://www.linuxquestions.org/questions/linux-networking-3/bizarre-tcp-connectivity-issues-from-certain-clients-totally-mystified-771804/)
The site shows the Wireshark output/errors - and these might be similar to what you're seeing.  If not, then ignore what I've pasted.

Good luck!  Keep us informed. :)

Wireshark faults were like this:
server_ip_addr         client_ip_addr         TCP      http > 26027 [ACK] Seq=1356 Ack=2764 Win=11712 Len=0
server_ip_addr         client_ip_addr         TCP      [TCP segment of a reassembled PDU]
client_ip_addr         server_ip_addr         TCP      26027 > http [ACK] Seq=2764 Ack=2808 Win=32128 Len=0
server_ip_addr         client_ip_addr         TCP      [TCP Previous segment lost] [TCP segment of a reassembled PDU]
server_ip_addr         client_ip_addr         TCP      [TCP segment of a reassembled PDU]

client_ip_addr         server_ip_addr         TCP      [TCP Dup ACK  25#1] 26027 > http [ACK] Seq=2764 Ack=2808 Win=32128 Len=0 SLE=2816  SRE=4268
server_ip_addr         client_ip_addr         TCP      [TCP Retransmission] [TCP segment of a reassembled PDU]
server_ip_addr         client_ip_addr         TCP      [TCP Retransmission] [TCP segment of a reassembled PDU]
server_ip_addr         client_ip_addr         TCP      [TCP segment of a reassembled PDU]
client_ip_addr         server_ip_addr         TCP      [TCP Dup ACK  25#2] 26027 > http [ACK] Seq=2764 Ack=2808 Win=32128 Len=0 SLE=2816  SRE=4276


Looks like some switch or router can't menage fragmented packets.
I would suggest to check fragmentation.
May be MTU is large?

To check MTU - edit and make permanent changes:
[http://ubuntuforums.org/showthread.php?t=1887063](http://ubuntuforums.org/showthread.php?t=1887063)

sudo ifconfig eth0 mtu 1458

Also:
[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

---

### Post by Hotshot5000 on 2012-04-10
I've already played a bit with the mtu and it doesn't seem to be the problem.

I thought about it and it looks like there is some kind of accumulation in some kernel caches that after 2 days block my connection to the google sites. I have a server written in java using openjdk that I start after I boot. This server basically waits in a selector.select() until it receives a connection on port 30003. My hypothesis is that after 2 days of waiting something happens in the kernel code because of this openjdk vm.

So I kill the server and still have problems with google.com. I go to sleep and after about 10 hours I come back(no restart of the computer) and google and related sites all magically work as if after a few hours some caches get cleared.

Now I will wait for 3-5 days without the server on and see if I get the problem again. If not it's clear that it had something to do with either my code or the VM implementation (and I don't think it's my code since I just create a selector and wait for keys that never come).

Now that I think about it every time this problem showed up was after I had the server running for a couple of days.

A jvm shouldn't influence the OS in these kind of ways should it? Could this be an OpenJDK bug?

---

### Post by Hotshot5000 on 2012-04-12
All my other sites are working fine but sometimes when I try to search something on google.com or use youtube or any google related services it remains in the connecting phase in firefox. Also nothing else works opera, chromium, wget, lynx... Looking into wireshark I see that it tries to connect to google but it keeps getting TCP previous segment lost and it never gets the site (or it gets it with a 5 minute delay).

Any ideas what could be wrong?

---

### Post by Ms. Daisy on 2012-04-12
How is your network configured? (example: desktop --> ethernet cable --> router --> cable modem)

---

### Post by Hotshot5000 on 2012-04-12
Yeah. I have a toshiba laptop connected through cable to a router that connects to the rest of the world through pppoe with a cable. The pppoe has a mtu of 1492 and ubuntu 1500 so I tried lowering in ubuntu with sudo ifconfig eth0 mtu 1492 but it still doesn't work. Or should I set it to 1464 (because of those 28 that get added)?

---

### Post by CharlesA on 2012-04-12
Multiple threads have been merged. Please do not post duplicate threads as it dilutes the community's efforts.

---

### Post by Ms. Daisy on 2012-04-12
Hotshot5000, now that your 4 threads have been merged you might want to write a **BRIEF** summary of what you've tried, what worked, what didn't work,  what errors you got, and what you have eliminated as possible problems.  I doubt anyone will be able to follow what has happened in the 4 separate threads (or frankly will want to read all 4 pages of this convoluted mess).

Post that summary here.

---

### Post by Hotshot5000 on 2012-04-12
OK.

I have a toshiba laptop from about 2008 connected through cable to a router (roline rotronic router almost no name since I couldn't find firmware upgrades). The router is connected to the isp through pppoe.

I cannot connect to google.com or any sites related to google.com such as youtube or sites that use google-analytics. It either times out or it finally connects after about 5 minutes in waiting. This behavior starts about 2 days after booting, so the first about 48 hours everything is peachy.

I have tried using firefox, opera, chromium, lynx, wget everything. Ping works and it's not a DNS problem since I tried the google 8.8.8.8, 8.8.4.4 addresses and it doesn't help in any way.

I also have a java server that listens on 30003 using openjdk. Initially I thought it might have something to do with this so I kill the server and in about 12 hours the connection to google.com starts working again. But then after 2 days it's no longer working again. So my hypothesis was wrong.

I tried restarting the router. Nothing. Modified the mt from 1500 to 1492 like on the pppoe on the router. Nothing. Tried 1464. Now no sites work. Back on 1492, everything works except google.

I install wireshark and see that when I wait for google to load I get a lot of TCP previous segment lost errors to google ip. The dns keeps trying different google servers with different ips but all have the same problem: TCP previous segment lost. After a few minutes it either times out or it finds a server that responds. But if I try again then I have to wait another 5 minutes.

Rebooting the sytem works. For 2 days that is. Using windows both xp and 7 doesn't exhibit the problem. Other windows machines on the network don't exhibit the issue. I closed all other machines so that I am alone connected to the router. Nothing. After a few hours it might start woking again all by itself and after another couple of days it starts having the problem again.

I reinstalled the system from scratch. Formated even the home partition hoping it was some damn configuration file. Still can't connect.

Using startpage.com instead of google.com or google.ro (I am from Romania) works.

I had the system working for months when I installed some updates including a kernel update a couple of months ago. From then on ubuntu 11.10 started exhibiting this problem. I do not remember what kernel version it was but I updated to 3.2 I think after I tried the precise pangolin beta and it still exhibited the issue.

Last thing I tried now: I got rid of the router and connected directly to internet using pppoe configuration from ubuntu. Guess what now google and everything else works. I got back behind the router and you guessed it: everything works except google. So it seems there is some bad interaction between my ubuntu and that router! But then again it worked for months and windows xp and 7 both work like a charm. Any ideas what the kernel programmers might have changed in the tcp stack?

Should I report it as a bug?

---

### Post by matt_symes on 2012-04-13
Hi

Can we recheck your mtu ? Please post the output of

```
cat /sys/class/net/eth0/mtu
```

Kind regards

---

### Post by Hotshot5000 on 2012-04-13
Right now it's 1500 but everything works... We will see in about 2 days if this still holds true though.

---

### Post by matt_symes on 2012-04-13
Hi

> **Hotshot5000 said:**
> Right now it's 1500 but everything works... We will see in about 2 days if this still holds true though.

It's always worth checking when it goes off. I just wanted to double check what it was set as.

Are you sure the mtu on the router is 1492 ? Try 1492 or even lower to stop fragmentation in the kernel.

Are you using path mtu discovery ?

```
cat /proc/sys/net/ipv4/ip_no_pmtu_disc
```When you set the MTU did you do it in the kernel ? How did you change that value ?

Have a read of this.

[http://www.netheaven.com/pmtu.html](http://www.netheaven.com/pmtu.html)

Kind regards

---

### Post by Hotshot5000 on 2012-04-14
That command returns 0. So it's activated.

I've read that article and I already knew that issue. I'll try to disable the discovery next time I encounter the issue, but I don't think that is the problem since the packets i receive when having the problem are around 74 bytes each, so they're not even close to 1492 to pose that problem from the article.

The router is 1492 for sure I just checked again in the router settings. Nothing changed here.

I changed the mtu using both the network manager from automatic to 1492 in wired connection edit menu and also using sudo ifconfig eth0 mtu 1492 or other values for temporary changes when testing to find a workaround. The thing is if I just reboot in Ubuntu or Windows it works just fine again. In windows I don't get the problem but in ubuntu I will get it the next day or so.

Also why would google servers block the icmp notifications for mtu? Isn't that a mistake on their part?

---

