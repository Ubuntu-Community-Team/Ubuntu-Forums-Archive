---
title: "How to open a port for Torrent Downloads"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by ramuk on 2009-09-22
[CENTER][FONT=Arial Black][COLOR=Red]**[SIZE=5]Yet to be solved[/SIZE]**[/COLOR][/FONT]
[/CENTER]


Hi there,

Am struggling with a problem from a long time now. The problem is as follows 

Am downloading torrents using[COLOR=DarkRed] Transmission 1.74(8994) in UBUNTU 8.10.[/COLOR] My torrents are downloading at a low speed, so I googled and tried some of the windows tricks on Ubuntu. But those all failed my attempts. Still Transmission Displays this all time classic message "port is closed". No matter whatever port I choose. 

Iam having a Broadband connection(256 kbps) from a Good ISP in our country(INDIA) which can give 1.4 kbps at nights and on Sunday's(TATA Broadband Service). am having a router/modem Telenet (TPE 3015) provided by my ISP.

[COLOR=DarkRed]Check the image Below and give me some details on... how to fill it, to open a port in my router/modem.[/COLOR]

[COLOR=SeaGreen]Thanks in advance. Dear open friends.[/COLOR] :)

[IMG]http://img19.imageshack.us/img19/4079/router01.png[/IMG]
|
|
|
Even knowing that, posting here may solve my problem. I was hesitating unnecessarily to post. At least am here now... before I die with it not being solved. :D
|
|
|

---

### Post by pete.urban on 2009-09-22
Hi!

I think you could fill the first line with these parameters:

I don't know what kind of applications could you choose there (in the applicatins column)
the inbound and private ports should be the same, that transmission using
the private ip is the IP that your machine is using
enable it
save and than check the port...

I hope I can help you with this!

---

### Post by Bucky Ball on 2009-09-22
- Enable the first one, (1.)
- name it, 
- not sure what 'Other' menu has in it,
- 'Inbound Port' the port number you want open
- 'Both' should work for type (although you are better to get the one it is)
- 'Private IP' should be left at 0.0.0.0
- 'Private port' same as 'inbound port' (port # you want open)

Hope that helps. 

Strange as Transmission normally configures what it needs to. Some providers will slow down P2P connections; yours may be one of them. Are you getting good speeds with everything else?

Don't hesitate to ask, that's why the forums are here. :)

---

### Post by ramuk on 2009-09-23
Thanks for the quick reply (Bucky Ball & pete.urban). But am not at home. when I return I'll Follow what U told, and post the result here.

Sorry I was in a bit hurry when I was posting. Here is the Drop-down list showing the possible things it has.
[IMG]http://img228.imageshack.us/img228/8328/router02.png[/IMG]

             I've another doubt. If I leave IP at all Zeros(0) does it work without any security problem. I read on other forums that it should be my current IP. But am having a Dynamic IP. So what should I do now ?

[COLOR="DarkRed"]Just my brother called me, and I told him to do the above. He said that, it is not accepting if the IP is left at all Zeros.[/COLOR]

Thanks in Advance Dear Open Friends.

---

### Post by pete.urban on 2009-09-23
Ramuk!
I think you should leave the application menu "other"! Than if you do what we mentioned.
The IP must be define, because  I think there is no  computer on your LAN (I think there isn't ;) )  your computer got always the same address from the router. It woked in  my room with 3 PCs.

regards,
peter

---

### Post by ramuk on 2009-09-24
hi pete,

           Transmission is still showing that the port is closed. What to do now. I did all what "U" & "Bucky Ball" said. See the image I attached.

[IMG]http://img195.imageshack.us/img195/1610/router03.png[/IMG]

and this too.......
**This is the Transmission Preferences Window.**

[IMG]http://img41.imageshack.us/img41/5797/transmissionpreferences.png[/IMG]

|
|
|
:oops: [COLOR="Red"]Sorry friends, I know this is a dumb question .:oops:  I don't know How to Use this(any) forum. Am completely new, and am having problem in finding my own post. First I need to search for my thread and then look for replies and then am replying. So is there any direct way to open my Posts/threads.[/COLOR] :oops:

---

### Post by wojox on 2009-09-24
Click on administration and see if you have UPnP.

---

### Post by blackened on 2009-09-24
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129586&d=1253783280[/IMG]

---

### Post by ramuk on 2009-09-24
Wow.:D thanks for such quick reply Friends.

I tried that too "_[COLOR="Red"]blackened[/COLOR]_", but still it is giving the same "Port Closed" message. :confused:

[COLOR="Red"]_wojox:_[/COLOR]

Where can I find Administrator in Transmission? :confused:

---

### Post by wojox on 2009-09-24
It's on the router. :lolflag:

---

### Post by blackened on 2009-09-24
Ah well. Figured I would kill two birds with one stone: check if UPnP was enabled, and use that if it was. No harm though.

**Ramuk:** Is yours the only machine on this network?

---

### Post by bruno9779 on 2009-09-24
I had a router of that family, and with Ktorrent's upnp plugin I entered the router config just to make sure all was good.

I would really like a gnome interface for ktorrent. Transmission is so lame

---

### Post by ramuk on 2009-09-24
**[COLOR="YellowGreen"]_bruno9779_:[/COLOR]**
Thank god. I found someone with same hardware.:)
Can u tell me where is UPnP in the router if U found it.

**_[COLOR="Red"]wojox[/COLOR]_ & _[COLOR="DarkRed"]black[COLOR="Black"]ened[/COLOR][/COLOR]_:**
Friends... I searched for uPnP option on my router, I didn't found it anywhere. :(

**_[COLOR="DarkRed"]black[COLOR="Black"]ened[/COLOR][/COLOR]_:**
No. I don't have any system at home. I Use a single system In Dual Boot mode With XP and UBUNTU 8.10.

**NOTE:**  (Maybe of help) I've same problem in XP too.

**_[COLOR="Red"]wojox[/COLOR]_ & _[COLOR="DarkRed"]black[COLOR="Black"]ened[/COLOR][/COLOR]_:**
(Maybe of some help) here are the images to know what is in all those Menus.

 [SIZE="4"]01[/SIZE]
[IMG]http://img19.imageshack.us/img19/2404/01cpewimax.png[/IMG]

 [SIZE="4"]02[/SIZE]
[IMG]http://img195.imageshack.us/img195/5126/02cpelan.png[/IMG]

 [SIZE="4"]03[/SIZE]
[IMG]http://img41.imageshack.us/img41/6213/03cpefirewall.png[/IMG]

 [SIZE="4"]04[/SIZE]
[IMG]http://img198.imageshack.us/img198/9397/04cpeadmin.png[/IMG]
|
|
------------- ( Thanks for Your time friends ) -------------
------------ ( Sorry, if am wasting your time ) ------------
|
|

---

### Post by ramuk on 2009-09-24
Sorry friends, am taking more time to reply. Because am spending some time to take screen-shots, edit them to correct size and getting rid of unnecessary things in them and all. **so that anyone with same problem can follow it clearly**.

---

### Post by bruno9779 on 2009-09-24
upnp is a client that automatically forwards ports. If you have it, it is in linux, not in the router.
Its function is: port forwarding without messing with the router.

I can't help you much with transmission, but if you want to give ktorrent a go, then, after installing go to:

preferences > plugins 

in ktorrent and install pnp plugin.

at this point a new dialog in preferences will let you configure it real easy.

In my ktorrent i can see the brand and model of the router as soon as it is plugged, without configuring anything.

I also advise the "protocol encryction" option.
works great with my ISP

---

### Post by pete.urban on 2009-09-24
> **NOTE:**  (Maybe of help) I've same problem in XP too.What Kind of firewall do you use for the WinXp? (zone alarm, comodo or windows firewall?) and what is the torrent client? (utorrent, bitcomet. azureus? )

p.s.:
I think the IP you got from the ISP is not the same as the IP of your computer. If it is right, than we have to figure out how to create a virtual server for your torrent client. After that you should use the same port in windows XP and in Ubuntu.

regards,
peter

---

### Post by ramuk on 2009-09-25
**[COLOR="YellowGreen"]_bruno9779:_[/COLOR]**

I already have ktorrent installed.:D

[COLOR="Gray"][I]> I can't help you much with transmission, but if you want to give ktorrent a go, then, after installing go to:

preferences > plugins

in ktorrent and install pnp plugin.[/I][/COLOR]

Sure.:) I have same problem in kTorrent also... if u are happy to help, am ready to try.

[SIZE="5"]1.[/SIZE] [COLOR="Red"]I've Installed the UPnP Plug-in also but still its not Giving me full speed. And I notice that Download speed is LESS every time (mostly, with or without Plug-in and even in transmission) But Upload speed is to its fullest for a long-times.[/COLOR] :confused:

[COLOR="Silver"]*> at this point a new dialog in preferences will let you configure it real easy.*[/COLOR]

[SIZE="5"]2.[/SIZE] [COLOR="Red"]Do you mean Port? How?[/COLOR]
[COLOR="Silver"][I]
> 
In my ktorrent i can see the brand and model of the router as soon as it is plugged, without configuring anything.[/I][/COLOR]

[SIZE="5"]3.[/SIZE] [COLOR="Red"]How to Find my model through kTorrent?[/COLOR]

[COLOR="Silver"]*> I also advise the "protocol encryction" option.*[/COLOR]

:) [COLOR="Green"]Thanks for the suggestion. I've already Enabled encryption after installing.[/COLOR]

---

### Post by ramuk on 2009-09-25
[COLOR="Navy"]_**[SIZE="3"]pete.urban:[/SIZE]**_[/COLOR]

[COLOR="Gray"]> *What Kind of firewall do you use for the WinXp?*[/COLOR]

No dedicated firewalls. I have F-Secure Antivirus, provided by my ISP. It has its own Firewall. But I opened a port Using the "Open port" option in F-Secure Firewall.

[COLOR="Gray"]*> .....and what is the torrent client?*[/COLOR]

utorrent. (same problem here. Sometimes I can see [COLOR="YellowGreen"]green[/COLOR] tick mark but with in few minutes it turns to [COLOR="DarkOrange"]Orange[/COLOR] and sometimes [COLOR="Red"]Red[/COLOR] Exclamation. But it is comparatively faster than UBUNTUs-Torrent Clients. Because it downloaded a slow downloading torrent in UBUNTU-transmission, faster in XP-utorrent.  But still I want to solve this problem in UBUNTU. Even UTorrent downloads only at 21kBps. but actually my speed is 1Mbps at nights that means nearly 120-130KBps)

[COLOR="Gray"]> 
*I think the IP you got from the ISP is not the same as the IP of your computer. If it is right, than we have to figure out how to create a virtual server for your torrent client. After that you should use the same port in windows XP and in Ubuntu.*[/COLOR]

Yes! My IP is not same! :mad: (as per [www.whatismyip.com](www.whatismyip.com)) What to do now ? :( Help me Friends. Do something :confused:

---

### Post by bruno9779 on 2009-09-26
> **pete.urban said:**
> 
I think the IP you got from the ISP is not the same as the IP of your computer. 


This is not right. Your IP on Local Area Network (from your router inwards) is from the private range:
usually 192.168.x.x (class C). More info _[here]("http://en.wikipedia.org/wiki/Private_network")_

The IP on Wide Area Network (the internet, from your router outwards) is from the public IP range (almost any IP not in private range) and it is usually fixed by your ISP.

I think you should try and set the port forwarding in your router by hand.

your entries on the router port forwarding should look something like this:

	
	192.168.1.11	KTorrent UPNP 0 - TCP Any -> 6881	Active	
        192.168.1.11	KTorrent UPNP 1 - UDP Any -> 6881       Active
        192.168.1.11	KTorrent UPNP 1 - UDP Any -> 4444       Active

this entries are made by UPNP, on my local IP 192.168.1.11 that is assigned by DHCP (dynamic IP).
If DHCP were to assign a different IP to me, upnp would re-forward the ports, but in your case it may be wise to fix your actual private IP.

Edit connections in network manager, and go to the IPv4 tab.
Here change "method" to manual. and then add an entry, with 192.168.1.1 as gateway.
IP and subnet mask you get by running in a terminal:

```
bruno@bruno-box:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:1d:8d:b7:d9  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0

```

You will have also to set the DNS servers manually, using your ISPs or some open ones, like [http://www.opendns.com]("http://www.opendns.com")
 (208.67.222.222 and 208.67.220.220)

---

### Post by ramuk on 2009-09-26
:confused: Friends am in total confusion now. My ISP's Customer Care tells that I have a Dynamic IP which should be the same as what i see on my system. But I see a IP with '192.' series in my system, and they tell that they see a IP with '10.' series and When I searched for my IP using [www.whatismyip.com](www.whatismyip.com) it displays '59.' series.

Now how can I download Torrents at Max Possible speed. :(

---

### Post by ramuk on 2009-09-26
[I]> your entries on the router port forwarding should look something like this:


192.168.1.11 KTorrent UPNP 0 - TCP Any -> 6881 Active
192.168.1.11 KTorrent UPNP 1 - UDP Any -> 6881 Active
192.168.1.11 KTorrent UPNP 1 - UDP Any -> 4444 Active[/I]

How to see router port forwarding (sorry, am on windows now but I will restart and Switch to UBUNTU)

---

### Post by bruno9779 on 2009-09-26
the private IP range is:

class A : 10.x.x.x
class B : form 172.16.0.0 to 172.31.255.255
class C : 192.168.x.x

---

### Post by bruno9779 on 2009-09-26
in the first post you wrote you pasted a screenshot. There you set your por forwarding.

i have found a link of an howto for a similar router and utorrent: [TPE-3015]("http://portforward.com/english/routers/port_forwarding/Telenet/TNDSL-2120/Utorrent.htm")

---

### Post by ramuk on 2009-09-26
[COLOR="YellowGreen"]_bruno9779:_[/COLOR]

:(I think all the clients or unfortunately a bunch of clients from my area are behind some sort of Proxy or something.(still on windows am restarting now. So Ill be online within 15 mins)

---

### Post by ramuk on 2009-09-26
> [I] Re: How to open a port for Torrent Downloads
in the first post you wrote you pasted a screenshot. There you set your por forwarding.

i have found a link of an how to for a similar router and utorrent: TPE-3015[/I]

Your Link displayed Some AD Site

---

### Post by ramuk on 2009-09-26
OK. am on linux Now :)

:oops: U link should be this

[http://portforward.com/english/routers/port_forwarding/Telenet/TNDSL-2120/Utorrent.htm](http://portforward.com/english/routers/port_forwarding/Telenet/TNDSL-2120/Utorrent.htm)

instead of this
 
[http://http//portforward.com/english/routers/port_forwarding/Telenet/TNDSL-2120/Utorrent.htm](http://http//portforward.com/english/routers/port_forwarding/Telenet/TNDSL-2120/Utorrent.htm)

---

### Post by ramuk on 2009-09-26
> [I]in the first post you wrote you pasted a screenshot. There you set your por forwarding.

i have found a link of an howto for a similar router and utorrent: TPE-3015[/I]

I tried it already. It didn't worked for me. :( May be  because of Unsure IP

---

### Post by wojox on 2009-09-26
You still fighting with this thing? Hold on let me check some resources.

---

### Post by ramuk on 2009-09-26
**[SIZE="3"]_[COLOR="Red"]wojox[/COLOR]_:[/SIZE]**
Thank god :D U came back :guitar:
please read all of my replies regarding this problem in this post, So that U can Point me in Right Direction if Possible(I hope).

---

### Post by wojox on 2009-09-26
What version of transmission are you using?

Open Edit > Preferences > Network and set the Listening Port to: 51413

And check Use UPnP or NAT-PMP

Close it reboot and go to  [http://www.torrentz.com/search?q=ebooks+linux](http://www.torrentz.com/search?q=ebooks+linux)

Try to download a book. Remember it takes a little bit to start connecting.

---

### Post by ramuk on 2009-09-26
[COLOR="Silver"]*> What version of transmission are you using?*[/COLOR]

Transmission 1.74(8994)


> [I][COLOR="Silver"]Open Edit > Preferences > Network and set the Listening Port to: 51413

And check Use UPnP or NAT-PMP

Close it reboot and go to [http://www.torrentz.com/search?q=ebooks+linux](http://www.torrentz.com/search?q=ebooks+linux)

Try to download a book. Remember it takes a little bit to start connecting. [/COLOR][/I]

Yes Ill do it and Ill reply soon.

---

### Post by ramuk on 2009-09-26
Changed and going to Reboot. Ill be back in a moment.

---

### Post by ramuk on 2009-09-26
am downloading a small 13MB file. but how can I find the average download speed. it is changing its number between 9 to 25KBps. As it is afternoon 1:30 for me here, I get only 30KBps speed from My ISP. So, I should check for speed at NIGHT. I get 120KBps at Nights and Sundays.

---

### Post by ramuk on 2009-09-26
By-the-way what is a good torrent site


Check these peers

[IMG]http://img85.imageshack.us/img85/3181/peers.png[/IMG]

---

### Post by wojox on 2009-09-26
It says Downloading from ? of ? Connected peers

I like [I][COLOR=Silver][http://www.torrentz.com]("http://www.torrentz.com/search?q=ebooks+linux") 


[/COLOR][/I]

---

### Post by wojox on 2009-09-26
I like [I][COLOR=Silver][http://www.torrentz.com]("http://www.torrentz.com/search?q=ebooks+linux") 


[/COLOR][/I]

---

### Post by wojox on 2009-09-26
Something is weird, I get like 400 kb/s

---

### Post by ramuk on 2009-09-26
I can see, at average, may be it is downloading at 50+% speed nearly 15 or 17KBps speed. I'll check in the night and I'll Post the results. tomorrow.

Should I change the port in my router too.

But I don't think doing so may not help me. Because those IPs are different at Different Places, like I have a Different IP at Home, Customer care tells me a Different IP and [www.whatismyip.com](www.whatismyip.com) Displayes a Different IP. :( :confused:

---

### Post by ramuk on 2009-09-26
oops! :oops: Power is out. It may take some time to come online (1-2 hours).

Thanks friends. Ill post results tomorrow. bye.

---

### Post by ramuk on 2009-09-27
**[SIZE="3"]Hi _[COLOR="YellowGreen"]wojox[/COLOR]_.[/SIZE]** :)

**[COLOR="Red"]_But still, I may need help from you all_.[/COLOR]**

Thanks for your time. I think, I figured out where the problem is...(Only for the Present torrent - **See image**). The torrent am downloading at present is not having the seeds which it is showing **(SEE IMAGE)**. it is completely opposite. It is having 1 or 0  seeds/leeches Most of the time **_(Based on seedpeer.com)_**. so its worthless to download. **_But I Doubt For Someone is getting more speed_** **(See image 2)**.

**But still, I have Port Closed problem** which is effecting my speed. Uploads are OK, But Downloads are not **(SEE IMAGE)**.

Here is the Screen shot.
**[SIZE="4"]1.[/SIZE]**
[IMG]http://img25.imageshack.us/img25/5379/utorrentdetails.jpg[/IMG]

[SIZE="4"]**2.**[/SIZE]
[IMG]http://img33.imageshack.us/img33/3636/utorrenti.jpg[/IMG]

---

### Post by ramuk on 2009-10-25
[quote=ganeshcp][I]Hi,
I own a tata indicom wimax connection and own the same modem as you do. I came across your post and have been wondering for ages how to access the modem's router settings? I don't know the modem router ip or how to find it! Can you please help! I'm from xxxxxx. 

Pls do email me. 
Thanks. 

Ganesh[/I]  [/quote]

Hi Ganesh.

O:) First-of-all... am happy to see someone around, from my Nation; in UBUNTU forum. 

     OK. Now... Lets get into the topic. So You have a Wimax modem, provided by TataIndicom Broadband service, and you want to change the router settings..... Here-you-go.

[COLOR=Red]1.[/COLOR] Open a new Browser window (Ctrl+t OR Ctrl+n - in FireFox)
[COLOR=Red]2.[/COLOR] But. First double click on the "Local Area Connection" Icon in your system-Tray (that two monitors Icon) and Click on the Support Tab.
[COLOR=Red]3.[/COLOR] Now see, what is the IP set in your system and
[COLOR=Red]4.[/COLOR] post the IP here to help me, help you find the correct Router IP.

OR

[COLOR=Red]4.[/COLOR] For example You found something like this "245.143.4.2"
Then type
--------------
245.143.4.1
--------------
in your address bar and press enter. 
[SIZE=3][FONT=Arial][COLOR=Red]**5. Now... have fun. _But mind not to change something_ _You can't fix_ _or_ _You don't Know_.**[/COLOR][/FONT] O:)[/SIZE]

---

### Post by ramuk on 2009-10-26
> [I]Hi Ramuk,
Thanks for the reply.

I have gone through the thread...but what I'm in need of the IP to the modem router. No where I can find how to access the modem router settings.

Ganesh[/I]

Ganesh...

To login to router, you need the router IP and that is one less than your IP. So please message me or post your IP here. so that I can help you better.

and one more thing are you a static IP holder or You have Dynamic IP.

---

### Post by ramuk on 2009-10-26
OR Try this 192.168.0.1 once

---

### Post by Bucky Ball on 2009-10-27
Or try getting the manual for your router and finding the correct IP to get into the Config GUI. The make and model will be on the router.

192.168.0.1 is common but depends on brand.

---

### Post by fosterz on 2009-10-27
i guess it takes bydefualt a port or else u can also do manually editing in KTorrent or ne torrent package

---

### Post by tortuka on 2009-11-19
hi ramuk,
i am also having the same ISP and router made (TATA and TELENET TPE3015 ).

and i am having the same problem as ganesh,

but i can access my router's page when i release the ip address,
but after that, i cannot get the major options of NAT and virtual servers and that...

and main thing is that, the default gateway isnt working when router is on, and i am also getting the different ip addresses...

i am also hoping to get a good help in this matter...

and one thing, i am using xp and not ubuntu...

---

