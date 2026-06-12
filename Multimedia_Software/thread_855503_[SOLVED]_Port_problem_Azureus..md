---
title: "[SOLVED] Port problem Azureus."
date: 2008-07-10
forum: Multimedia Software
---

### Post by diwas on 2008-07-10
Hello there. Im in a desperate need of a p2p software. I downloaded Azureus but cannot configure the port of incoming peer connection. The screenshot is attached. 
Please help me out.
Thank you.


PLUS another question. I used to use Ares in XP. It had a good service, i mean i could find almost everything i searched. So will installing Azureus also give me the same thing? Im told by someone that p2p doesnt depend upon the software. All the peers are same. Is this true? If yes, this solves my query.

---

### Post by cozmicharlie on 2008-07-10
The screenshot shows the port that Azureus will use through your router.  You can change it to anything you like but really there is no need to.  What you have to do is open the port in your router.  You do that by doing what is called "port forwarding".  This web site should help [http://www.portforward.com/](http://www.portforward.com/).

Yes, whoever told you that is correct.  A bittorrent is only a client and you can access any tracker or peer.

Post back if you are still having problems.

Enjoy!

---

### Post by diwas on 2008-07-11
This looks promising but my router isnt here. 
Its TPLink 8817.
8810 is included though.

---

### Post by cozmicharlie on 2008-07-11
It may be the same.  If it is a fairly new router then it should have a very easy method for port forwarding.  You could check the documentation that came with the router.  Basically though you follow these steps:

you will need the following:
Access to your router
Your computer IP address (the one you are installing Azureus on)
The port - 23933

Access your router via your web browser (Firefox).  You should have a router IP that you gives you access to the router - something like 192.101.1.1.  It then will ask you for your user name and password.  You should have those in the documentation.  If you have never changed your password then the username/password for most routers is admin/admin (if you have not changed it you should for security).  In the router it should have something like "port forwarding" or it may be under security.  It will have a place to type in the application name (azureus), the port (23933)and the IP address of the computer.  It should also have something that requests udp/tcp - you can do both.  Once you enable port forwarding you should be able to test it in Azureus.

---

### Post by diwas on 2008-07-11
No, there is no option called port forwarding in there. Neither udp/tcp. But there is a tab named NAT. But it wont enable, i dont know why, may be im in a bridge mode.

And how to see my static IP address?? 

One information: The router is set in windows XP. And later in ubuntu by sudo pppoeconf. Its in the bridge mode. VPI/VCI is 8/81. If u need any further information about this, please ask me.

---

### Post by cozmicharlie on 2008-07-11
Does your router interface look like the one for the 8810?  Is it like the one here ([http://www.portforward.com/english/routers/port_forwarding/TP-Link/TD-8810/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/TP-Link/TD-8810/Azureus.htm)).  If so then you should be able to follow the instructions for the 8810.  If not then it appears that you open the router in the browser and go to advanced setup>NAT and click the "Add" button.  You enter the following info:
custom server:  (whatever name you want to give it) Azur2
server ip address (your address)
External port start 23933
External port end 23933
protocol tcp/udp

that should do it

You can find your ip in windows: open the control panel>network and internet connections>right click on the icon for the wireless>status>support (or if you have an icon in your taskbar just right click on it).  In Ubuntu I believe the command is "ifconfig" (open a terminal and type ifconfig at the prompt.

---

### Post by diwas on 2008-07-12
ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:18:46:01:4e:e3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:46ff:fe01:4ee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1859027 (1.7 MB)  TX bytes:550124 (537.2 KB)
          Interrupt:20 Memory:ff8ffc00-ff8ffcff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95000 (92.7 KB)  TX bytes:95000 (92.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.1.217.134  P-t-P:10.1.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1726732 (1.6 MB)  TX bytes:459402 (448.6 KB)

---

### Post by diwas on 2008-07-12
> **cozmicharlie said:**
> Does your router interface look like the one for the 8810?  Is it like the one here ([http://www.portforward.com/english/routers/port_forwarding/TP-Link/TD-8810/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/TP-Link/TD-8810/Azureus.htm)).  If so then you should be able to follow the instructions for the 8810.  If not then it appears that you open the router in the browser and go to advanced setup>NAT and click the "Add" button.  You enter the following info:
custom server:  (whatever name you want to give it) Azur2
server ip address (your address)
External port start 23933
External port end 23933
protocol tcp/udp

that should do it

You can find your ip in windows: open the control panel>network and internet connections>right click on the icon for the wireless>status>support (or if you have an icon in your taskbar just right click on it).  In Ubuntu I believe the command is "ifconfig" (open a terminal and type ifconfig at the prompt.

The interface is quite different. I have attached a screenshot. There is PVC0 or smthg here and its deactivated. No matter which PVC i put on, its deactivated. So the interface doesnt quite match wid the 8810 router.

---

### Post by cozmicharlie on 2008-07-12
I am not sure how to access it in the router.  Just click and open the tabs and see if one has port forwarding.  Also, there is a help button that probably has instructions or there is a guide for the router here [http://www.tp-link.com/support/download.asp?a=1&m=TD-8817&h=Annex%20B](http://www.tp-link.com/support/download.asp?a=1&m=TD-8817&h=Annex%20B)

---

### Post by diwas on 2008-07-12
Thank you. I have downloaded the User manual, and here it seems like i have to remove the bridge mode and enable PPPoE/PPPoA or smthg like that. After doin this, this screenshot appears ONLY ON PVC0.
The screenshot is here.


EDIT: initially, router was in a bridge mode.

---

### Post by cozmicharlie on 2008-07-13
Thats it - now all you need to do is add the information IP, port number (the start port and end port are the same - 23933), tcp/udp.  Once you open the port then start Azueres - in the menu go to tools>NAT/firewall test and test your connection.  If the port is open it should read "OK".  If so you are ready to go.

---

### Post by diwas on 2008-07-13
Im sorry, but u know what?? My internet has stopped working in Ubuntu and im here in XP. Its the same internet connection in the same box. I did "sudo pppoeconf" again but still no work. 

Another thing. Like in XP when u connect it shows "Connecting through WAN miniport.." "verifyin user name and password" "registerin ur computer on the network" and finally "authenticated". In ubuntu though "sudo pon dsl-provider". It just shows that smthg is loaded but no error message or confirmations. Isnt there anyway to see at which stage did the thing went wrong??

---

### Post by cozmicharlie on 2008-07-13
Are you connecting via a wireless or a lan?

---

### Post by diwas on 2008-07-14
Its via LAN. The internet is not working. I dont know what did this. I rebooted the modem with factory default settings and applied with my own then saved it. But still it wont work. 

I fount something though. I can check out the statistics of connection through "plog".

---

### Post by diwas on 2008-07-14
diwas@diwas-desktop:~$ plog
Jul 14 18:43:05 diwas-desktop pppd[5841]: Plugin rp-pppoe.so loaded.
Jul 14 18:43:05 diwas-desktop pppd[5843]: pppd 2.4.4 started by root, uid 0
Jul 14 18:43:05 diwas-desktop pppd[5843]: PPP session is 6044
Jul 14 18:43:05 diwas-desktop pppd[5843]: Using interface ppp1
Jul 14 18:43:05 diwas-desktop pppd[5843]: Connect: ppp1 <--> eth0
Jul 14 18:43:05 diwas-desktop pppd[5843]: CHAP authentication failed: Account is occupied
Jul 14 18:43:05 diwas-desktop pppd[5843]: CHAP authentication failed
Jul 14 18:43:05 diwas-desktop pppd[5843]: Connection terminated.

diwas@diwas-desktop:~$ ifconfig ppp0

ppp0      Link encap:Point-to-Point Protocol
  
          inet addr:10.1.232.172  P-t-P:10.1.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:7584 (7.4 KB)  TX bytes:749 (749.0 B)




Here's what i get in the terminal when i execute the commands.

---

### Post by cozmicharlie on 2008-07-14
> **diwas said:**
> diwas@diwas-desktop:~$ plog
Jul 14 18:43:05 diwas-desktop pppd[5843]: CHAP authentication failed
 

This has to do with configuring the login name and password or that the authentification mode of your ISP is not CHAP. Normally it's just a question of pass and login, but it could also happen, that yout ISP uses PAP instead of CHAP (It's normally PAP).

Not sure why you need to do all this.  Do you have DHCP set up?  Most routers all you need to do is plug them in - you don't have to set up manually.

---

### Post by diwas on 2008-07-15
Well, it was working all fine till the day i changed the bridge mode to PPPoA/PPPoE and saved it...went to NAT and saw (the screenshot is already uploaded). Then again changed the PPPoA/PPPoE to bridge mode...not sure what to do and saved it again. The internet was working fine till then. But when i rebooted the system...it stopped working. 
I havent changed anythin, thus im very suprised as what could be the problem. Its working fine in XP, wid the same router of course.

---

### Post by cozmicharlie on 2008-07-15
This is beyond my knowledge.  Since your post was about Azureus you should post another thread with your specific router problem as the subject.  I am afraid because of the thread title know one will come along to help you with the router.  Post another thread with your router issue then once you get that fixed come back to this one and we can continue to work on Azureus.  Sorry I can't be of more help.

---

### Post by diwas on 2008-07-16
Thank you. I appreciate your help very much.
Ok i will post a new thread now, coz its really gettin too much using XP.

---

### Post by diwas on 2008-07-19
Ok, the internet's working now...I just pressed the "reset" button. Hehe.

So lets get back to this topic...One thing BTW, Bittorent is working very fine. Now i just need a p2p thing like ares in windows. I guess azureus is just Bittorent not p2p. Isnt it?


BTW iam using "transmission" for bittorent and it looks perfect!

---

### Post by cozmicharlie on 2008-07-19
> **diwas said:**
> Ok, the internet's working now...I just pressed the "reset" button. Hehe.

So lets get back to this topic...One thing BTW, Bittorent is working very fine. Now i just need a p2p thing like ares in windows. I guess azureus is just Bittorent not p2p. Isnt it?


BTW iam using "transmission" for bittorent and it looks perfect!

Ah - sometimes it's the small items that escape us.

No bittorrent is not p2p. I am not exactly sure what this is "i just need a p2p thing like ares in windows".  Do you want to share your music with friends so others can access your files?

---

### Post by diwas on 2008-07-20
No its the reverse actually. I want to acquire the "shared file" of other users. Specially music, its really important. Azureus is just a bittorent client isnt it?? Well transmission also does the same thing (is there any difference between them?).
And can you refer me any p2p software??

---

### Post by cozmicharlie on 2008-07-20
Azureus and transmission are both bittorrent clients so basically they do the same thing.  The difference is the options and plug ins available.  Azureus is based on Java so it works cross platform (Windows, Linux, Mac) and it also has lots more plug ins so you can do more with Azurues but both are basically bittorrent clients.  Which one you use is generally just personal preference.  If all you need is basic bittorrent then Transmission works fine.

OK - I googled ares and I see what you are looking for.  Ares is a filesharing network.  It does use bittorrent protocol but it is a private network.  Azurues or Transmission would work but the network is set up so you have to use the Ares client.  There are ways to set this up in Linux but I don't think they are really working very good and I would not recommend them.  I am not sure if you could set this up through Wine (Wine lets you run some windows programs in linux).  The closest Linux program I could find is Nicotine ([http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)).  You can install it through Synaptic.  You should do some searching in the forums (search p2p or ares etc) because there may be others I am unaware of.  Nicotine looks to me like what you are looking for though.  FYI, you don't need this to find music to download - there are plenty of private and public trackers available depending on what kind of music you like.

---

### Post by diwas on 2008-07-20
How can i download the musics then????

---

### Post by cozmicharlie on 2008-07-20
> **diwas said:**
> How can i download the musics then????

Do you mean from Nicotine or using Transmission?

---

### Post by cozmicharlie on 2008-07-20
Also, what kind of music or videos do you want to download?  I can recommend some bittorrent sites if I know what you like.

---

### Post by cozmicharlie on 2008-07-20
Your post got me interested in what you are doing so I did some research and found another site that is just getting started but looks like it is exactly what you are interested in.  Their is an article on TorrentFreak that describes it here [http://torrentfreak.com/p2p-next-introduces-live-bittorrent-streaming-080718/](http://torrentfreak.com/p2p-next-introduces-live-bittorrent-streaming-080718/) and the site is here [http://trial.p2p-next.org/](http://trial.p2p-next.org/).  It's still beta but it is Linux compatible.  The difference between this and normal bittorrent is you can also stream.

Also, since you have Azureus you may be interested in Vuze [http://www.vuze.com/app](http://www.vuze.com/app).

Though if you just want to download you can do that with Transmission - as above, let me know what type of music you like and I can point you to a good Bittorrent tracker.

---

### Post by diwas on 2008-07-21
I use mininova.org for torrents. Which one do u prefer...(for music and softwares, windows software). My taste for music varies. But mostly im into metal, rock, heavy metal, alternatives, slow sentimental, etc.

---

### Post by cozmicharlie on 2008-07-21
OK - minova is good.  The site I sent (torrentfreaks) has lists of all the top torrent trackers.  

Personally, I prefer private trackers that share lossless formats only.  I am a Deadhead so I go to a number of Grateful Dead sites but for more general music and video I like the following:

The Traders Den ([http://www.thetradersden.org/](http://www.thetradersden.org/))
Zomb Torrents ([http://zombtracker.the-zomb.com/](http://zombtracker.the-zomb.com/))
Dime ([http://www.dimeadozen.org/](http://www.dimeadozen.org/))
Tapecity ([http://www.tapecity.org/](http://www.tapecity.org/))
etree ([http://bt.etree.org/](http://bt.etree.org/))
Internet Archive ([http://www.archive.org/details/audio](http://www.archive.org/details/audio))
For Grateful Dead/Jamband - Lossless Legs is the best ([http://www.shnflac.net/](http://www.shnflac.net/))

These are all private trackers so you have to sign up for an account but they are all free.  All of them are also only trade legal torrents.  All of these are accessible with Transmission or Azureus.

---

### Post by diwas on 2008-07-21
Thank you sir for your help...i really appreciate it. But guess what?? i ran ARES under WINE and it worked!!! It did. Well, i got the software i wanted hehehe...try that software...i think u will like it too...u dont have to search in the websites for the songs....or videos or movies..its all there.

Thank you for the support.
BTW is there anythin i cud do to boost up the torrent's speed??? coz its somewhat slow. For instance
normal download rates are arnd 15kbps but torrent's download rate is arnd 10kbps....i used the torrent wid max seeders and min leechers but the effect is the same...its there any problem??


And yeah hehe...thank god i ddnt go that deep into port forwardin...hehe i dont know what wud be the consequence if i did that...

---

### Post by cozmicharlie on 2008-07-21
Great - glad to hear it is working under Wine.  I think a lot of people will be interested in this so mark the thread solved.  If you had to do anything special to get it running in Wine you may want to note that in the thread so others won't have any trouble getting it set up.   

As per the port speed.  Usually it has to do with your isp and the torrent site.  As long as you don't have your ports blocked or a firewall then you should be able to get good speed.  The Azureus web site has a lot of good info on settings - even though it is Azurues much of the info is the same no matter what client you are using.  Read through this [http://www.azureuswiki.com/index.php/Main_Page](http://www.azureuswiki.com/index.php/Main_Page).  It also has links to sites for testing your connection speeds.

Great to hear you are another satisfied Ubuntu user!

Enjoy

---

### Post by diwas on 2008-07-22
The thread is marked as solved (Im very glad...hehe)

I ddnt konw 1 thing. Well I thought bittorent's speed depends entirely upon the upload bandwidth of the seeders and leechers...but u mentioned torrent sites. Iam confused. My concept abt bittorent is wrong i guess. 
I would also like to download DVDrip movies u know (Im a big fan of em) so which syt shud i join? 

Here is the list i wud like to have for bittorent (accordin to the neccesity)
1. Music (Metal, Alternative, Thrash, Heavy Metal, Rock and Roll...)
2. Softwares (hehe...windows illegal ones)
3. Movies (high quality but low file size...arnd 700mb or less)

Thats it...tell me the xact syt u use for the above list, coz ur xperienced and u know exactly which syt to look for em. hey we cud continue talkin even if the problem is solved isnt it??

---

### Post by cozmicharlie on 2008-07-22
Bittorrent does depend on the seeders speed.  When using bittorrent the actual files do not reside on a server but on every persons computer that is seeding the file.  In order to download those files though you need a "torrent" file (the torrent file is not the music or video file).  That is were the various bittorrent tracker sites come in.  They host the torrent files.  The speed does depend on the seeders and on your available bandwidth through your isp.  This is a good explanation [http://dessent.net/btfaq/](http://dessent.net/btfaq/).

As per sites - a really good source of info on bittorrent is torrentfreaks (see link in another post).  As per trackers, youtorrent ([http://www.youtorrent.com/](http://www.youtorrent.com/)) is a good place to start.  It is not a tracker but it is a search engine that searches all the trackers for the torrent you are looking for.  So you type in whatever video or music you are searching for and it tells you which tracker is hosting the file.  That way you don't have to search each tracker individually. There are other sites like youtorrent ([http://torrentfreak.com/top-10-youtorrent-alternatives-080414/](http://torrentfreak.com/top-10-youtorrent-alternatives-080414/)).  Here is a list of the top torrent sites ([http://torrentfreak.com/top-torrent-sites-ranked-by-google-080704/](http://torrentfreak.com/top-torrent-sites-ranked-by-google-080704/)).  For music I recommend the sites I listed in the previous post (Dime, Zomb, The Traders Den, Tapecity, The Internet Archive).  These are all sites that try and maintain a high quality of lossless music and videos.

Yes - just because it is marked solved does not mean you can't continue to post.

Enjoy

---

### Post by diwas on 2008-07-22
This is good. I read the "about bittorent" page and found out all the stuffs. It has a good advantage over p2p like ares that its not quite limited. Well...so all i need to do is register and the file is rightaway!! 
Thanks for the help...im already downloadin the movie Across The Universe...i think it will complete in 2 days(pausin and resumin of course).
hehe.

---

### Post by cozmicharlie on 2008-07-22
Great - do you have all the packages needed to play the video and music files installed?

---

### Post by diwas on 2008-07-23
Yes, i have installed all the codecs and it works great. But 1 thing abt ubuntu the flash stuff in webpages are pretty messed up...The animations are slow and consumes more memory(i havent calculated but iam sayin abt system performance when playin flash stuff). Other than that...its pretty cool.

---

### Post by diwas on 2008-07-24
Well a serious bug or the mechanism but Transmission really annoys me with it. Whenever i download any torrent two colored lines appear blue and yellow. As per my knowledge, the blue one is VERIFIED data and the yellow is UNVERIFIED data. If i have to pause and restart the computer, the unverified data is lost!!! Damn thats too bad esp for slow internet connection like the one i have. Today i downloaded abt 200mb and then i had to restart now the download is again starting from 40mb. Thats ********!!!

Well on downloading with azureus the download rate is tooo slow, 2KBps. I have a screen shot attached. Well i could have downloaded the torrent wid Ares, but i figured out a defect of it under WINE. It takes too long to connect...
Well have a look at it. 

Thank you.

---

### Post by cozmicharlie on 2008-07-24
Not sure why Transmission is doing that.  I don't use it.  I would recommend you switch to Deluge.  It looks like Azureus (and works like Azureus) but does not have the resource requirement of Azureus.  It is probably the most popular BT client in Linux.  You can install from Synaptic. Here is an article about it in Lifehacker [http://lifehacker.com/381098/deluge-does-lightweight-bittorrent-across-platforms](http://lifehacker.com/381098/deluge-does-lightweight-bittorrent-across-platforms).

As per speed - you can look through the articles mentioned here and see if anything might help.  [http://lifehacker.com/398962/speed-up-your-bittorrent-downloads](http://lifehacker.com/398962/speed-up-your-bittorrent-downloads)

---

### Post by diwas on 2008-07-24
It works great!! Deluge works!! haha. the download rates are arnd 11kbps which is accepted.

---

### Post by cozmicharlie on 2008-07-24
Great - that's why its the most popular BT client for Linux.

---

### Post by diwas on 2008-07-24
Yeah i read abt it too. But tell me smthg, y does Azureus has to be so complicated????

---

### Post by cozmicharlie on 2008-07-24
Its called the "life cycle of a product".  They start out sleek and simple then people keep requesting new functions so they add them and eventually the app becomes bloated.  Also, it is written in Java which takes a bit more resources to run.  Though the advantage is you can use it across platforms (Linux, Windows, Mac).  I still use Azureus and I like it but I mainly do so because of a couple plugins I like.  Azsmrc allows full access over my home network so I can add a torrent from any of my computers and the HTMLwebUI plugin lets me access Azureus over the internet if I am traveling.  I have a dedicated Eeepc (with a 500 gb usb drive attached) with a highly tweaked version of Hardy installed that I use as a BT box so I don't really care how much memory it uses.  I like the EeePC because it draws so little power and I can keep it running 24x7.  I stick it in a closet and forget about it.  For just basic BT though Azurues is not a good choice.

---

### Post by diwas on 2008-07-24
Oh yes it isnt, now with deluge it seems like i dont have any problem...i have a torrent just drag and drop and it will do the rest of its stuffs. But Transmission really annoyed be today...200mb is a big deal man for 128Kbps bandwidth. Haha.

Well, if i ever feel the need of the plugin i will surely switch to Azureus...but now im happy wid deluge...haha.

---

### Post by diwas on 2008-07-26
hey, 
Deluge is great but it is doin the same thing. Like when i download besides the DOWNLOADED there are two numbers...no brackets and another within brackets. The one without bracket is the verified data and inside that is unverified data (though i havent read abt it...). So when i pause the download and restart the computer, the number inside the bracket vanishes...only number outside remains and downloading starts frm thre...
Its the same problem like wid transmission isnt it?? How can i solve this?? Coz im loosing of hundreds of megabyters here....

---

### Post by cozmicharlie on 2008-07-26
> **diwas said:**
> hey, 
Deluge is great but it is doin the same thing. Like when i download besides the DOWNLOADED there are two numbers...no brackets and another within brackets. The one without bracket is the verified data and inside that is unverified data (though i havent read abt it...). So when i pause the download and restart the computer, the number inside the bracket vanishes...only number outside remains and downloading starts frm thre...
Its the same problem like wid transmission isnt it?? How can i solve this?? Coz im loosing of hundreds of megabyters here....

Can you attach a screenshot.  I will load Deluge in my system and see if I can duplicate it but I need a screenshot so I know what to look for.

---

### Post by diwas on 2008-07-27
This is the screenshot i took day before yesterday but explains everything i guess. Well the megabyte inside the bracket vanishes if i have to restart the computer...and next time download starts frm the megabyte not enclosed within the bracket.

---

### Post by cozmicharlie on 2008-07-27
I am not exactly sure what you are looking at.  Do you mean the 311 mib (110.9 mib)?

Are their seeders for this torrent?  

The problem may be the folder you are downloading to. If it is owned by root then Deluge may have problems accessing it.  Try setting up your download folder in your home/yourname directory and see if that makes a difference.

---

### Post by diwas on 2008-07-27
Yes, exactly 311 mib (110.9 mib) is what im talkin abt.

The place where the torrent downloads is the window's NTFS folder. Is it the reason?? I have half downloaded...so changin the folder will start the torrent frm the beginnin. and i dont have sufficient memory in my filesystem...its just 4gb and well only 400mib is free. But do u think changing folder will solve the problem?

---

### Post by cozmicharlie on 2008-07-27
Is the device you are downloading to (the one that is ntfs) an exteernal usb ard drive or something similar?  It could be the problem so if it is an external drive you could reformat to fat 32,

First though, you have enough room to run a test.  The file is 311 and you have 400.  So, download it to this drive and see if you get different results.  If  the problem is not present when you download to the 4 gb drive then that will confirm the problem.  If not we need to look for something else causing this.

If it turns out that is the problem then you should reformat the drive and yes you will loose all the data.  But, if you save the files you will not have to start all over.  One, we get to that point I can explain how to do this so you don't have to start over.  You just need to remember to save the files.

I will be out most of the day today so I may not get back to you until tonight.

---

### Post by diwas on 2008-07-27
Its my hard drive not xternal drive. I have only 1 hard drive...and these (includin the root) are its partitions. 

The other day i had downloaded a complete software abt 240mib in transmission(that is befre i downloaded and started usin deluge)...in my root partition...the problem was still there.

---

### Post by cozmicharlie on 2008-07-27
> Its my hard drive not xternal drive. I have only 1 hard drive...and these (includin the root) are its partitions. 


So are you dual booting or using Wubi?  I don't think it is a problem with ntfs as much as the permissions.

> The other day i had downloaded a complete software abt 240mib in transmission(that is befre i downloaded and started usin deluge)...in my root partition...the problem was still there.

I think that is the problem. Your home/yourname folder is owned by you and not root.  I had a similar problem with Azureus not finding the files when I rebooted.  It turned out it was because I was downloading to a hard drive using ntfs that was owned by root.  I reformatted the hard drive to ext3 and changed the permissions.  

In your case, your home/yourname folder should be owned by you so if you use a folder in home/yourname to test with we can determine if that is the problem.  Usually, trying to figure these issues out is a process of elimination. You should have a home/yourname/music folder - try downloading to that folder and see if it behaves the same or if that fixes it.  Once we know that is the problem then we can figure out a permanent solution.

---

### Post by diwas on 2008-07-27
Iam dual bootin XP and Ubuntu. XP's drives are all formatted to NTFS. There are 3 drives or lets say partitions coz all of em are frm the same Hard Drive. Ubuntu is ext3.

OK i will test by downloadin abt 200mib file into that folder and let u know abt the behavior.

I have another problem here. My sda5 doesnt mount since yesterday when i installed NTFS configuration tool. It says "You are not priviledged to mount the volume 'Music'. Here 'Music' is sda5. I used to mount it by clicking it from Places>Music. Now it wont mount. I havn't changed anything in the NTFS configuration tool...
Though out of topic...but is there any solution for that?

---

### Post by diwas on 2008-07-28
Well here are the two screenshots. U can see the path its /home/diwas. In the 2nd screen shot, the 18mib inside the bracket just vanishes. Only the one outside remains. The 2nd screen shot was taken after restarting the computer.

---

### Post by cozmicharlie on 2008-07-28
OK - their is no problem.

> In the 2nd screen shot, the 18mib inside the bracket just vanishes. Only the one outside remains. The 2nd screen shot was taken after restarting the computer

When you download, you have the two statistics "download" and "upload".  The download is the one that deals with your files (the files you have downloaded to your computer).  So for example using the data from the Metallica show.  The total file is 111.7 mb.  You have downloaded 16% of the file (18.6 mb).  That is the % of the files on your computer.  

In the first session (screenshot on left):
Downloaded 18.6 (18.6)  - that means you have downloaded a total of 18.6 mb and in this session you downloaded 18.6 mb.  

Now you stop and restart your computer and you get screenshot 2 (the one the right).
Downloaded 18.6mb (0)  -  you still have the 18.6 mb of the files on your computer but since you are starting a new session it goes back to (0) in the brackets.  It does not mean you are starting over from (0) (you can check how much of the file has downloaded by going to the file tab).  It only means you have not downloaded anything yet during that session.  The 18.6 mb of files is still on your computer.  

It is the same for the Upload row.  Uploading is how much of the files someone has uploaded from your files.  Thus you have downloaded 18.6 mb and uploaded 2.1 mb (note the share ratio - upload/download is .112 (2.1/18.6).  Generally, a good share ratio is 1 (that means you have shared the file with at least 1 other person).  That is the idea behind bittorrent - everyone shares.

So there is no problem.  The behavior you are getting is perfectly normal.  Isn't that nice!  The (0) just means you have started a new session - it does not mean you are starting over downloading the files.

Enjoy

---

### Post by diwas on 2008-07-28
DAMN......it was not a problem then...damn!!! Hahaa....i was soo foolish. Hehe....thanks for helpin...otherwise i wud still be wonderin abt the thing..

Hehe...how on earth cud my internet be so fast....hehhe i was addin the two megabytes...hehe.

---

### Post by diwas on 2008-07-28
DAMN......it was not a problem then...damn!!! Hahaa....i was soo foolish. Hehe....thanks for helpin...otherwise i wud still be wonderin abt the thing..

Hehe...how on earth cud my internet be so fast....hehhe i was addin the two megabytes...hehe.

---

