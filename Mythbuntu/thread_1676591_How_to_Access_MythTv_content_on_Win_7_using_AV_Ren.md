---
title: "How to Access MythTv content on Win 7 using AV Renderer"
date: 2011-01-27
forum: Mythbuntu
---

### Post by nhtrader on 2011-01-27
Can anyone point me to a resource that explains how I can accessed my MythTv content using a Win7 computer on my home network?

My win7 sees a MythTV AV Renderer, but I don't know how access the content.

---

### Post by newlinux on 2011-01-27
Are you using media player in Win7? If you want to access your mythtv content via UPnP on Windows you should get a compatible client.

[http://www.mythtv.org/wiki/UPnP_Client_Info#Software_UPnP_Clients](http://www.mythtv.org/wiki/UPnP_Client_Info#Software_UPnP_Clients)

Is a start. there is also a windows Mythtv port, but I don't know what shape that is in.

XBMC works well on windows and can access mythtv content reliably. Worst case, you could simply access the mythtv recordings and videos directly over the network in windows (you could use mythlink.pl to give recordings useful human readable names).

Don't use windows too often at home, but I am getting a Tablet PC with windows 7 on it - maybe I'll play when I get it.

---

### Post by AlecJ on 2011-01-27
> **nhtrader said:**
> Can anyone point me to a resource that explains how I can accessed my MythTv content using a Win7 computer on my home network?

My win7 sees a MythTV AV Renderer, but I don't know how access the content.


double click on the AV renderer icon, this should open media player.
down the left hand side you should see the MYTH AV renderer appear as a drive, click on it
you can now see the icons for Music, Recordings, etc
in Recordings, click on a file and watch the recording.

Can't stream live TV, but you can set a program to record and then watch it in time delay over the network.

Hope that helps

---

### Post by nhtrader on 2011-01-27
I tried to double click it, but nothing happened. I also tried to right click it, but the options shown didn't apply. That's when I started this thread. Nothing appeared; no content from MythTV.

But I have to say that I did change one setting in Windows "Networks". I turned on "Network discovery for files and printers", but nothing changed at that time.

Well, that was earlier in the day. 

Now I come back hours later and try again after reading your post.

However, since clicking on it didn't work earlier in the day didn't work. I decided to open Windows Media Center (WMC) and see if I could find MythTV and add it to the library. In fact, WMC did see it. And on my first attempt I added it to WMC's Recorded TV library. This didn't work. My guess is that WMC is looking *.wtv files, which of course there are none. MythTV's default format is *.mpg. So, I removed it from Recorded TV and added it to WMC's Video Libary. And viola, the Tv recordings from MythTV are there and I can play them. However, there is a problem. No all of the recordings work. They all play fine when I use MythTV frontend, but so far it looks like only 50% of the recordings play using WMC.

Then I decided to exit WMC and try accessing MythTV-PC using the network feature of Win7, and I saw the hostname of the MythTV-PC appeared. I then clicked on it, and MythTV's "recordings" folder appeared. Now of course I double click the files and they play. But again, not all files play using Win7, but all files do play on MythTV.

As for the MythTV AV Renderer, I no longer see it. It has disappeared.

BTW, here's another quirk. I'm currently recording a program with MythTV and the program hasn't ended yet. But when I access that program with Win7 it plays, but it doesn't update. In other words, it doesn't function as a PVR. The program plays only up to the time when I selected the show. So when I exit the program and start it again, the program is 5 minutes longer, but again, it will not continue streaming the content when I use Win7. I guess this is an example of streaming LiveTV, which you mentioned is not allowed.

---

### Post by AlecJ on 2011-01-27
I too had recordings that did not play and stayed as air balloons icon's, I found that it is quite slow and if you leave it on the recordings page, the icons slowly start to populate, 30min's should see all present and correct, and I have a 1GB network so maybe longer.
I also have 24000 mp3's, they took ages to process, it's not called Windoze for nothing.

Glad you have it working, sort of

If your looking for a proper remote frontend, you can always boot the win 7 machine from the mythbuntu live cd, as long as you have set a password and set both IP addresses in the General backend page. There are a few other ways as well from the cd or stick.

---

### Post by nhtrader on 2011-01-28
Yes, I'm interested in proper remote frontend. Actually I'm experimenting with MythTV's capabilities.

1. I want remote access via local network. 
2. I want remote access via internet.

In the latter case, rebooting with Live CD is possible. However, in the first case it isn't. 

My local network configuration at the moment is ....

PC1 = Win7 running media center with dual tuner card and connected to Home Theater
PC2 = Mythbuntu 10.10 (32bit) with single tuner card (which is able to record 2 programs simultaneously b/c  comcast is sending multiplexed signal) connected to local network.

So, my problem is not being able to reboot PC1. The good news is that I can now view of PC2's content from PC1. Now, I'm trying to gain full access to PC2 while running Win7.

As for setting up passwords in MythTV to allow remote database access. Well, that's next. 


BTW, the MythTV AV Renderer reappear this morning. I don't know why it comes and goes. 

Also worth noting, is that during the installation process there was a prompt that allows the user to select various services. So I selected SSH, NFS, Samba, & MythTV. Maybe this is why I can access MythTV's files. Maybe I'm accessing them through a samba server rather than through MythTV's UPNP (AV Renderer).

---

### Post by AlecJ on 2011-01-28
It's not possible to have a frontend running on windows for mythtv yet, may never be?

So if you want a frontend on the local network you will have to boot into myth or run myth within windows (which seams pointless) but I have never tried.

_samba_ only allows you to share the folders once you have Mapped the drive to a letter in win 7:- 
 /var/lib/mythtv/Music mapped to M: in win 7
or a Linux _nfs_ share as setup in /etc/network/samba/smb.conf mounted by fstab at boot or manually with 
sudo mount 192.168.?.?:/path/to/share /path/to/local/folder
_SSH_ allows you to connect from remote machines with a graphical or terminal with
 ssh mythtv@192.168.?.?         or    ssh -X mythtv@192.168.?.?
MYTHTV allows you the AV service you using now.
_VNC_ allows a virtual desktop of your myth box on any remote pc, but no good for watching TV, I don't have a keyboard or mouse plugging into my box so VNC is vital for setup and tinkering.

If you want to stream over the Internet you will need a static IP from your ISP and good luck with that one..

my system has a dual core amd 64 3 or 4 Ghz ish processor, the mother board has 4 pci slots full of Nova DVB-S cards, all coaxed up to an old sky dish with a quad LNB retro fitted.
So 8 inputs, each card can supply 2 channels from the same multiplex simultaneously.
The onboard sound card feeds a 5.1 digital coax input on a 5.1 PC amp speaker system, remote control is via a MCE usb recivier and handset.
There is a Nvidia pic-e card with HDMI output to a LCD HDTV, using a HDMI cable.
3 TB hard drives for media and 1 300Gb holding the system. 1 TB drive is external USB at present.
The onboard 1Gb network socket to a 1Gb router links the remote front-end's and Internet.
All this lives in a rack type server case under the TV, with a lockable CD and panel, great for keeping little fingers out, and enough space for silent cooling.

one remote frontend is and old IBM thinkpad with a 16Gb SDcard on an 2.5 IDE converter for a hard drive, running mythbuntu frontend only. the sound from the laptop is fed into an old sony HIFI with 9" speakers and 50watts!
This lives on the kitchen window ledge, giving full live TV, recordings, Music, and Video's to the kitchen. This can be wireless, and was for a time, but her blackberry presents on the network forced me to run a cable out there.

The second is my acer 17" laptop booted on a usb myth stick, that we use in the garden in summer.

I do use win 7 but only for DVDfad to rip DVD's to the Video folders used by myth, it's great there are no DVD's or CD's in the front room anymore, all ripped to the system.

it's a good hobby as well.

---

### Post by newlinux on 2011-01-28
> **AlecJ said:**
> It's not possible to have a frontend running on windows for mythtv yet, may never be?


As I mentioned above, there is a windows port project, but I don't know what shape it is in - there also used to be a mythtv player app for windows, but I don't know if it has been updated to support the later version protocols - a quick google says it can be forced to work with .24. I used it a while back, and it's a basic interface for playing recordings and worked okay on XP.

Mythtv Player: [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)


Mythtv on windows: [http://www.mythtv.org/wiki/MythTV_on_Windows](http://www.mythtv.org/wiki/MythTV_on_Windows) and [http://code.google.com/p/mythtv-for-windows/](http://code.google.com/p/mythtv-for-windows/) 

Looks like you'd have to compile it yourself though...



> ...
If you want to stream over the Internet you will need a static IP from your ISP and good luck with that one..

You don't have to have a static IP. You you can use a Dynamic DNS service - there are plenty of free ones. Your bigger problem will be bandwidth and security. Perhaps just stream using the flashplayer in mythweb for Internet.

Probably the best/stable frontend for mythtv in windows in XBMC. It isn't fully featured, but it integrates fairly well, plus it is nice looking.

---

### Post by AlecJ on 2011-01-28
Just had a look at Mythtv Player: [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)

very interesting but looks like it can't do anymore that win 7 media player can do now, which is a shame.

Is the Xbox thing relevant, sorry not a gamer don't have an Xbox, would that run on win 7?

---

### Post by newlinux on 2011-01-28
> **AlecJ said:**
> Just had a look at Mythtv Player: [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)

very interesting but looks like it can't do anymore that win 7 media player can do now, which is a shame.

Is the Xbox thing relevant, sorry not a gamer don't have an Xbox, would that run on win 7?

I did say it ran on windows in my earlier posts.
Being a gamer has nothing to do with XBMC. I'm not one either.  XBMC is a media center that originated as being written for the original xbox, but has long run on windows and Linux, and now OSX, iPad, AppleTV2, and iPhone4.

In fact, if one wasn't interested in recording TV, I'd say it is a better choice than mythtv as media center.

[www.xbmc.org](www.xbmc.org)

---

### Post by newlinux on 2011-01-28
Also, mythtv player does have some capabilities I believe streaming via UPnP with Win 7 media player can't do:

1. Use myth's Commercial skipping
2. Use myth's bookmarks
3. Delete recordings

Again, I haven't used it in a while though because I haven't used much windows computing in a while. that will change now that my new tablet PC has arrived. Currently putting ubuntu on it, but will dual boot with Win7 Pro 64 bit.

---

### Post by bb_145 on 2011-01-28
I used to use mythtvplayer, but recently switched to the Windows port of the mythtv frontend

[http://www.mythtv.org/wiki/MythTV_on_Windows]("http://www.mythtv.org/wiki/MythTV_on_Windows")

So far it has worked surprisingly well, though I was using an XP machine.  I haven't tried it on Windows 7.

---

### Post by AlecJ on 2011-01-28
> **newlinux said:**
> I did say it ran on windows in my earlier posts.
Being a gamer has nothing to do with XBMC. I'm not one either.  XBMC is a media center that originated as being written for the original xbox, but has long run on windows and Linux, and now OSX, iPad, AppleTV2, and iPhone4.

In fact, if one wasn't interested in recording TV, I'd say it is a better choice than mythtv as media center.

[www.xbmc.org]("http://www.xbmc.org")

Good stuff

---

### Post by nhtrader on 2011-01-28
Nice exchange going on here. Thanks for the ideas.

1. I already have dynamic DNS setup that I use for remote access. It works perfectly. Now I only have to test it with MythTV.
2. I thought I should take baby steps. As my first step I'm interested in using MythWeb and understanding it.
3. I downloaded XBMC but am holding off on install. I always prefer to explore what I have first before adding something new and I haven't explored MythWeb yet.
4. MythTV Player may be useful if it can play the other half of the recordings that Windows Media Player/ Media Center doesn't play. But for simplicity's sake, I'd prefer to figure out which codec I'm missing and add it. Using WMP or WMC is fine for playback. I can for go commercial skipping. Using 30 second skips is fine for me. And if I can get MythWeb to work, then I've got remote scheduling. LiveTV is very low on my list of priorities since I generally do not watch Live TV. 

With respect to MythWeb, what is the url that I should use to access MythTV from a remote computer?

---

### Post by AlecJ on 2011-01-28
point your browser at the IP address of the myth box on the local network.

I use a static IP for my box, and as I was unable to get the manual network setup working I did it the old way editing the files.

Mythweb is handy for setting up play lists and recordings, and arranging your channel numbers etc.

---

### Post by newlinux on 2011-01-28
http://<hostname with mythweb>/mythweb

As far as outside of your LAN, you'll have to forward ports appropriately on your router and use your DDNS.

---

### Post by AlecJ on 2011-01-28
> **newlinux said:**
> 
As far as outside of your LAN, you'll have to forward ports appropriately on your router and use your DDNS.

I don't use this but it's an area I would like too, can you expand this a bit, whats required.
I can't get a static IP from my ISP, so maybe this might be useful.

What port?
where is a free DDNS?

Thanks in advance

---

### Post by nhtrader on 2011-01-28
Found the URL after some googling....

Here's an explanation for other newbies. Note that you can use MythTV'a Contol Center | Select plugin and then install the MythWeb Plugin. MythWeb must be installed before these URLs will work.

URL for accessing mythweb from browser on same machine as MythTV
[http://localhost:80/mythweb](http://localhost:80/mythweb)

URL for remote access to MythTV from home network...
[http://192.168.0.100:80/mythweb](http://192.168.0.100:80/mythweb)  (replace 192.168.0.100 with your local IP address)
or
[http://mythtv-hostname:80/mythweb](http://mythtv-hostname:80/mythweb) (you can use the computername you assigned to the MythTV PC)

URL for remote access to MythTV from Internet...
[http://45.45.45.45:80/mythweb](http://45.45.45.45:80/mythweb)  (45.45.45.45 is your WAN IP. Use whatismyip.com to figure this out)

However, you will not be able to access your MythTV machine until you open the port to you PC. You need to enter you home router and enable port forwarding. You need to manually change some settings in your router that let it know that you want traffic from outside the home network to enter your home network. And you want that outside traffic to be sent directly to 192.168.0.100 (the ip address of the MythTV backend) on port number 80 (which is the default port for the apache HTTP server).

Also note that that your ISP may block all traffic on port 80 b/c they do not want residential customers to be running HTTP servers. So you may need to change the default port 80 to some other number (ex: 8080). (I don't know how to do this yet. But I'll take a guess and hint that the appache server configuration files would be a good place to start.)

In addition, most users have dynamically assigned IP addresses from their ISP. This means that you ISP can change your WAN IP at any time and if this occurred while your away from your home, you would not know what the new IP address is and therefore you would not be able to access your MythTV PC remotely. 

The way to prevent this from happening is to use dynamic DNS. Google it. There are many free choices which will allow you to map any changes that your ISP makes to your home IP address. This will allow you to maintain a connection to your home computer regardless if any changes to your IP address were made.

That should get you started.

---

### Post by nhtrader on 2011-01-28
AlecJ,

here's one service for you [www.dyndns.com](www.dyndns.com).

Some routers (netgear equipment) have a section for you to insert your account name and password. So look in your router's User Guide to learn more about port forwarding and using dynamic DNS. 

Basically, this is how it works. After you create an account and input your current WAN IP address. [www.dyndns.com](www.dyndns.com) assigns you your own personal URL such as alecj.dyndns.com . Then from anywhere on any computer, you can then use this URL to access your home computer. Just type [http://alecj.dyndns.com](http://alecj.dyndns.com) and your in.

Now don't forget you need to tell your home computer to grant you access so you may need to change a few files. Notably, if you're accessing a linux systems (ubuntu/kubuntu/etc), change your /etc/hosts.allow and /etc/hosts.deny.  For other OSes you need to consult with them.

Also you may need to activate some daemons, or service, so that your request for access will be granted. It's like you need someone home to recognize that you're knocking on the door. for example install openSSH then you can gain access to your home computer in terminal mode. Or you need to install VNC and activate it before you leave your house, so when you try to make a remote connection, the VNC server will respond to your request. 

Of course, I would assume that since you're in this thread that you want remote access to your home MythTV which I what I just figured out how to do.

---

### Post by newlinux on 2011-01-28
> **nhtrader said:**
> Found the URL after some googling....

Here's an explanation for other newbies. Note that you can use MythTV'a Contol Center | Select plugin and then install the MythWeb Plugin. MythWeb must be installed before these URLs will work.

URL for accessing mythweb from browser on same machine as MythTV
[http://localhost:80/mythweb](http://localhost:80/mythweb)

URL for remote access to MythTV from home network...
[http://192.168.0.100:80/mythweb](http://192.168.0.100:80/mythweb)  (replace 192.168.0.100 with your local IP address)
or
[http://mythtv-hostname:80/mythweb](http://mythtv-hostname:80/mythweb) (you can use the computername you assigned to the MythTV PC)

URL for remote access to MythTV from Internet...
[http://45.45.45.45:80/mythweb](http://45.45.45.45:80/mythweb)  (45.45.45.45 is your WAN IP. Use whatismyip.com to figure this out)

However, you will not be able to access your MythTV machine until you open the port to you PC. You need to enter you home router and enable port forwarding. You need to manually change some settings in your router that let it know that you want traffic from outside the home network to enter your home network. And you want that outside traffic to be sent directly to 192.168.0.100 (the ip address of the MythTV backend) on port number 80 (which is the default port for the apache HTTP server).

Also note that that your ISP may block all traffic on port 80 b/c they do not want residential customers to be running HTTP servers. So you may need to change the default port 80 to some other number (ex: 8080). (I don't know how to do this yet. But I'll take a guess and hint that the appache server configuration files would be a good place to start.)

In addition, most users have dynamically assigned IP addresses from their ISP. This means that you ISP can change your WAN IP at any time and if this occurred while your away from your home, you would not know what the new IP address is and therefore you would not be able to access your MythTV PC remotely. 

The way to prevent this from happening is to use dynamic DNS. Google it. There are many free choices which will allow you to map any changes that your ISP makes to your home IP address. This will allow you to maintain a connection to your home computer regardless if any changes to your IP address were made.

That should get you started.

All good stuff. A couple of points.

1. If you are connecting to port 80 via the web no need to put port :80 after the machine name - 80 is the default.

2. you don't actuall have to have apache listen to a different port to use a different port on your WAN. You can forward an alternative port (such as 8080) from the WAN to your :80 port on the mythweb machine on your LAN (provided your router allows you to do this). So anything outside your LAN going to port 8080 would be redirected to your myth's machine's :80 port (this would still bypass your ISP's port 80 restriction because to the Internet is port 8080). So no need to mess with apache unless you want to be able to use that alternate port on your LAN as well. If you wanted to do that you could just add the following to

/etc/apache2/ports.conf

Listen 8080

(or whatever port you wanted) and restart apache and there you go.

---

### Post by nhtrader on 2011-01-28
Awesome. Thanks for the heads up.

---

### Post by nickrout on 2011-01-28
mythfrontend runs on windows, why not use it? Download it here

[http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)

---

### Post by nickrout on 2011-01-28
It is NOT recommended to expose mythweb to the internet at large. It is insecure. You are likely to get hacked.

Use an ssh tunnel. You can do this from windows via putty or from the normal ssh client using linux.

And if you are exposing ssh to the internet, for heaven's sake install denyhosts.

---

### Post by nhtrader on 2011-01-28
> **nickrout said:**
> 

Use an ssh tunnel. You can do this from windows via putty or from the normal ssh client using linux.

And if you are exposing ssh to the internet, for heaven's sake install denyhosts.

I have another PC-kubuntu that I access via a remote windows PC using putty. And I have the hosts.deny and hosts.allow configured to restrict access. So I'm familiar with what you are suggesting, but I only use this for terminal mode access. I never knew that I can use a browser through this connection.

Do you know how to use MythWeb from remote WindowsPC using putty to access home MythTV? Can you explain how to do this?

---

### Post by nhtrader on 2011-01-28
> **nickrout said:**
> mythfrontend runs on windows, why not use it? Download it here

[http://members.iinet.net.au/~davco/]("http://members.iinet.net.au/%7Edavco/")


I found the same link earlier today, as I've been busy hunting/searching for ways to access MythTV. I've downloaded it and will be experimenting this. I'll let you know how it goes.

---

### Post by nickrout on 2011-01-28
> **nhtrader said:**
> I have another PC-kubuntu that I access via a remote windows PC using putty. And I have the hosts.deny and hosts.allow configured to restrict access. So I'm familiar with what you are suggesting, but I only use this for terminal mode access. I never knew that I can use a browser through this connection.

Do you know how to use MythWeb from remote WindowsPC using putty to access home MythTV? Can you explain how to do this?

In putty, from the remote machine, in the settings dialogue (from memory I don't have it right here) - set source port to something random - I use 1313, then set the remote port to 192.168.1.12:80 (assuming mythweb is running on 192.168.1.12).

Once you have established the ssh connection thru putty, go to your browser and go to the url localhost:1313 - the connection gets tunnelled to 192.168.1.12 port 80.

---

### Post by nhtrader on 2011-01-28
thanks. I get it now.  Your explanation is so much easier to understand.

---

### Post by newlinux on 2011-01-29
I tried running the windows mythfrontend on my win7 Pro 64 bit machine and I couldn't even get it to run. It would crash before starting up... That's generally my luck with Windows. No real biggy. I have Ubuntu installed on it too and it is now a very cool convertible tablet/notebook. Touchscreen and pen input and screen rotation are now all working in with Ubuntu after some tweaking.

---

### Post by newlinux on 2011-01-29
I did however, just install xbmc in windows with the mythbox plugin and that works well so far, except for liveTV doesn't yet work with .24 - but I don't need livetv.

---

### Post by nickrout on 2011-01-30
> **newlinux said:**
> I tried running the windows mythfrontend on my win7 Pro 64 bit machine and I couldn't even get it to run. It would crash before starting up... That's generally my luck with Windows. No real biggy. I have Ubuntu installed on it too and it is now a very cool convertible tablet/notebook. Touchscreen and pen input and screen rotation are now all working in with Ubuntu after some tweaking.

I have been able to get the frontend to run on two different win7 machines, but it failed on Vista (got to a blank screen and went no further).

I used the 0.24 build from [http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)

> I did however, just install xbmc in windows with the mythbox plugin and that works well so far, except for liveTV doesn't yet work with .24 - but I don't need livetv.

That is a good option too.

---

### Post by newlinux on 2011-01-30
> **nickrout said:**
> I have been able to get the frontend to run on two different win7 machines, but it failed on Vista (got to a blank screen and went no further).

I used the 0.24 build from [http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)



I used that build too - no luck. Anything special you had to do or did it just work? Not that I really care to run myth in windows I was just trying it out for the sake of knowing...

Edit: Also, what version of win7 (pro, home premium, starter, 32 or 64 bit) did you get it working on?

---

### Post by nickrout on 2011-01-30
Professional 32 bit. (pretty sure the other machine it worked on is the same).

I did change the mysql.txt file to put the correct mysql database ip address. Despite specifying the correct address in the setup program, it wasn't carried into the mysql.txt file. You can find it in windows explorer by putting %APPDATA%/mythtv in the address bar. Other than having to do that it appeared to work fine.

---

### Post by newlinux on 2011-01-30
> **nickrout said:**
> Professional 32 bit. (pretty sure the other machine it worked on is the same).

I did change the mysql.txt file to put the correct mysql database ip address. Despite specifying the correct address in the setup program, it wasn't carried into the mysql.txt file. You can find it in windows explorer by putting %APPDATA%/mythtv in the address bar. Other than having to do that it appeared to work fine.


Thanks - I did that before, and I could verify that it was connecting, but the GUI would always crash almost instantaneously. I'm not going to play with it anymore. Given this is a dual boot machine and mythfrontend works fine in ubuntu and XBMC with mythbox works fine in win7 and ubuntu - I don't need it. I'll rarely boot to windows anyway...

Maybe something is up with win7 64 bit...

---

### Post by nhtrader on 2011-01-31
Well, I tried two pre-compiled binary versions of "Windows for MythTV" from 
   [http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)

1. 0.23-fixes
     This version crashed b/c it generated a network error immediately and the main menu never appeared. It stated that the Server was using network protocol 23056 and the client was using 56. I couldn't get past this error.

2. 0.23.1-fixes
     This version loaded ok. I got the main menu to display and I also could watch Live TV (SD & HD). But I couldn't do anything else. None of the Main Menu options worked, but these two menus crashed the program -  "Media Library" and "Manage Recordings" .

I tried these two versions b/c these matched the version that Mythbuntu 10.10 (32bit) comes with. It installed  0.23-fixes revision 26347 (Branches= /branches/release-0-23-fixes)

Note that latest version of MythTV (0.24) is not available as a pre-compiled binary. That process of creating a compiled binary seems too complicated for me.

BTW, I haven't yet compiled my own version MythTV for Windows for the same reason.

For those interested instructions can be found here...
    [http://www.mythtv.org/wiki/MythTV_on_Windows](http://www.mythtv.org/wiki/MythTV_on_Windows)

Haven't tried xbmc yet.

---

### Post by nickrout on 2011-01-31
> **nhtrader said:**
> Well, I tried two pre-compiled binary versions of "Windows for MythTV" from 
   [http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)

1. 0.23-fixes
     This version crashed b/c it generated a network error immediately and the main menu never appeared. It stated that the Server was using network protocol 23056 and the client was using 56. I couldn't get past this error.

2. 0.23.1-fixes
     This version loaded ok. I got the main menu to display and I also could watch Live TV (SD & HD). But I couldn't do anything else. None of the Main Menu options worked, but these two menus crashed the program -  "Media Library" and "Manage Recordings" .

I tried these two versions b/c these matched the version that Mythbuntu 10.10 (32bit) comes with. It installed  0.23-fixes revision 26347 (Branches= /branches/release-0-23-fixes)

Note that latest version of MythTV (0.24) is not available as a pre-compiled binary. That process of creating a compiled binary seems too complicated for me.

Are you talking about for windows or for *buntu?

For windows it is accessed off the same page as referred to above.

For *buntu it is available via the mythbuntu repos, and you SHOULD be using it.

---

### Post by nhtrader on 2011-02-02
> **nickrout said:**
> Are you talking about for windows or for *buntu?

For windows it is accessed off the same page as referred to above.

For *buntu it is available via the mythbuntu repos, and you SHOULD be using it.

For clarification I'm accessing a MythTV backend 0.23-fixes using ubuntu 10.10 OS using a remote PC running win7. 

I downloaded the windows version of MythTV on to the remote PC and tried two different versions available 0.23 and 0.23.1 as only a frontend.

The end result was that 0.23 allowed my win7 PC to only watch LiveTV. But it didn't behave properly when using ESC to exit - it froze/crashed. And I couldn't do anything else.

Using 0.23.1 with the default installation wasn't any better. However, the member who created these binaries offered a suggestion which was to delete the TERRA theme.

So I simply deleted the entire folder 

 C:\Program Files (x86)\mythtv\share\mythtv\themes\terra

And restarted Windows for MythTV Frontend on win7 PC. Now I had regained most of Frontend's functionality. I could now watch recording within Media Library which I couldn't do before. I could now enter Utilities/Setup|Setup Menu which I coudn't do before. Basically, I could use all of Frontend's menus which before caused the program to crash.

So despite the improvement, it is still not 100% compatible/functional on win7 using my hardware.

1.The ESC key doesn't work as expected exiting watching recordings or TV which causes it to crash/freeze.
2.MythMovies fails.
3.The Fast Forward and Rewind arrows work sporadically. You can hear that the audio track has been shifted but the video remains frozen on the last image displayed.

So removing the TERRA theme made improvements, but it's still not working as well as it does on ubuntu.

Despite this, it still avoids the main question which is how to use MythTV's AV Renderer that appears on the win7 PC.

---

### Post by newlinux on 2011-02-02
Maybe this will help:

[http://www.mythtv.org/wiki/UPnP_with_Windows_Media_Player](http://www.mythtv.org/wiki/UPnP_with_Windows_Media_Player)

---

### Post by nickrout on 2011-02-02
> **nhtrader said:**
> For clarification I'm accessing a MythTV backend 0.23-fixes using ubuntu 10.10 OS using a remote PC running win7. 



Why on earth are you still using 0.23? current is 0.24-fixes.

---

### Post by AlecJ on 2011-02-02
> **nhtrader said:**
> 
Despite this, it still avoids the main question which is how to use MythTV's AV Renderer that appears on the win7 PC.

It's just an icon for the UPnP server , if you left click on it and allow file and media share and setup the Homegroup on your win7 box.
A new icon shortcut will appear called whatevertv-decktop: MythTV AV Media Server, that when clicked opens a UPnP client, in this case windows media player. Then stream music and video but you have seen this already.

In the same way my Wifi Nokia can access it and download files from the Music folder and play them over bluetooth in the car.
I'm sure there is also an app somewhere that would allow my Nokia to play the videos and recordings as well?

It don't do nothing else, well apart from really annoyingly portraying mythical wonders of thus hidden usefulness.

---

### Post by nhtrader on 2011-02-04
Well, I just tried the AV renderer on another Win7 PC. This worked as expected. It figures.

Using Windows 7 PC: WMP
I clicked on Network. Refreshed Network. Windows found Renderer.
I opened up Win Media Player and selected Renderer
I selected Recorded TV | All TV - empty.
I selected Videos - TV shows appear (5 entries for every show)
Movies play fine but fast forward, rewind don't work.
TV shows play fine, and player controls work fine.

Using Windows 7 PC: WMC
 
I opened up Win Media Center and selected Recorded TV
Right Clicked Screen | Manage Library
Add folder from MythTV/recordings
No shows recorded by MythTV appear
Did the same for MythTV/Videos. Nothing appeared within WMC
Exited Recorded TV
Selected Pictures+Videos | Video Library
Right clicked screen | Manage Library
Added folders from MythTV/recordings + MythTV/video
Video Library now contains entry: MtythTV AV Media Server
All shows appear. But it too has 5 entries per show.

Playback is fine and player controls work fine.


Don't know why this second Win7 PC works and the first Win7 didn't.
Also don't know why each show has 5 entries.
Don't know why player controls don't work for Movies and time index shows movie length as 00:00.

As for using 0.24, well I'm only 2 weeks old with Mythbuntu/MythTV. I've  covered a lot of ground and I have a working system. This then allows  me to experiment and change hardware, and software, etc. Secondly, I've  also learned that 0.24 isn't available as a precompiled binary. So I  have more new stuff to learn. Plus I've learned that build 145 has video  playback problems so I was advised to use build 101. Again, learning  how to select a particular build is also another day's lesson. My goal  is to have MythTV working with all ubuntu/kubuntu/WinXP/Vista/Win7/Mac  machines. 

So I'm experimenting with the various ways to use MythTV on Windows.  Using AV Renderer when it works is simple. But as was demonstrated here,  it is frustrating to learn it may or may not work. And it still has  quirks (player conrols may not work, 5 entries per show, recorded TV  doesn't appear as recorded TV but as Video). Second option, using  windows for MythTV. Well, that's proving to be more complicated and  difficult. Stability is proving to be a problem. But the payoff of  course is full MythTV functionality. Third, I can boot from the  Mythbuntu CD and manually go through the settings each time. This again  isn't ideal.

---

### Post by newlinux on 2011-02-04
I was able to download .24 windows binary from the site above (I think this is what nickrout was referring to in his post above - that it was on the same page). It didn't work well for me though as detailed above. 

I think mythbox plugin for windows XBMC is an excellent alternative. It has a lot more functionality than the AV renderer. If nothing else is working for you, I'd give that a try. Works well for me - somewhat tricky part is that the recording directories have to be available on the windows machine (just map a drive). It was quick to setup (you can download the plugin from the xbmc interface). Bookmarking, fastforward/rewind, buffering playback (great for wirless connection on my laptop) editing recording schedules, skip commercials, view the program guide... On .23 (not .24) you can even watch livetv. It's almost a full featured frontend for mythtv and of course the rest of XBMC standard features (videos, weather, music, pictures) is probably overall better than myth's versions.

[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

---

### Post by nickrout on 2011-02-04
google "mythbuntu auto builds" and follow the instructions. It is a very easy upgrade to 0.24. 

You really won't get much support for outdated versions like 0.23.

---

