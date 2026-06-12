---
title: "Internet working just partly in Linux. In Windows, it's working fine."
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by alcatraz on 2009-04-23
Hello!

I have s very weird problem since a couple of days.
Some websites get a timeout. But the weirdest thing is, that some information "mostly only the Website title" can be loaded.
Sites which are not working for example: facebook.com or ebay.com.
I can ping those adresses, but I only get a PART (very small one).

Now the mysterious thing:
When I start in my Windows installation, it is working just fine!
I did install 9.04 today, still the same. My second notebook with 8.10 has the same problem.

What could that be? My only explaination is a kind of a protocol which can only be handled properly by Windows. But that is kind of impossible. Those things should be standardized.

By the way: I cannot install/update packages from the Ubuntu repositories.

Anyway, here some information:
Notebook #1:
Dell XPS 1340
Ubuntu 9.04, fresh installation

Notebook #2:
Samsung Q35
Ubuntu 8.10, old installation

Does anyone has an idea what the hack is going on there?

Greets,
Marc

---

### Post by ddrichardson on 2009-04-23
IPv6 would be the first thing I'd check, as its not enabled by default in Windows.

**Edit: Sorry [here]("http://wiki.lynxworks.eu/ubuntu/ipv6").**

---

### Post by GavinOB on 2009-04-23
I'm having similar issues. Some sites will only display text and no images (others are fine). I managed to disable ipv6 after upgrading to the 2.6.29 kernel and adding a line to grub, but it had no effect on the problem.

I tried using Firefox from the Live CD and the same sites will not load. I also tried other browsers (Opera, Epiphany). Strangely, there are no problems accessing the sites when running Windows.

Attached is a screenshot showing buzzfeed.com and the lack of images.

Other attempts to download missing images:
When inputting the direct URL of a missing image, I get the following error in Firefox: "Connection Interrupted The connection to the server was reset while the page was loading." Using wget, I get this error: "Read error (Connection reset by peer) in headers."

---

### Post by alcatraz on 2009-04-24
ddrichardson, I think you are right.
Everything what I read on the internet comfirms, that ipv6 is the problem here.
But as it seems, there is no way to disable ipv6 in Jaunty.

It is compiled into the kernel.
And echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6 does not work either.
The value after that is 1. But it does not work either. Maybe I have to enter it very early in a runlevel configuration? Before the networking initializations?

Greets,
Marc

---

### Post by ddrichardson on 2009-04-24
Yes, I know: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351656](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351656)

Try the method [here ]("https://answers.launchpad.net/ubuntu/+question/68420")for Firefox to confirm it is an IPv6 issue.

---

### Post by alcatraz on 2009-04-24
Hi!

I am currently not at home, so I cannot try it there.
But if it is the IPv6 issue, I don't know how to apply that patch :-S

---

### Post by ddrichardson on 2009-04-24
We'll worry about that when we need to.

---

### Post by alcatraz on 2009-04-24
I tried the Firefox thing.
There it is not working. So it isn't IPv6 what is messing here.
I was so sure about it. Because all signs pointed at that!

What else could be wrong here. Remember: It appears on 2 notebooks with 2 different installations (1x Jaunty, 1x Intrepid). This is a mystery :(

---

### Post by ddrichardson on 2009-04-24
How are you connected?

---

### Post by alcatraz on 2009-04-24
I am connected to my wireless router. Wireless and with cable.
Both the same reaction. Even if I connect directly to the connection where the router is connected.
When I go to the university with wireless, it is working just fine!

---

### Post by ddrichardson on 2009-04-24
Is your router using a non-standard set of ports?

---

### Post by alcatraz on 2009-04-24
It is using following ports:
TCP 21/21
TCP 80/80
TCP 443/443
TCP 53/53
TCP 25/25
TCP 110/110
TCP 23/23
TCP 500/500
TCP 1723/1723
TCP 1720/1720
TCP 800/800
TCP 1720/1720

But I don't think that it is a router problem. Because I connected directly to the Internet without my router: Same result

---

### Post by mossman44 on 2009-04-24
I have had several problems with the internet in Ubuntu 8.10. Sometimes it works fine but other times it has serious trouble resolving requests. I've tried several methods to disable ipv6 but none of them have worked. My internet connection works fine in windows as well as Debian Lenny so I'm led to believe it's an issue with Ubuntu. This annoying problem has kept me away from installing Ubuntu on my machine again so I've been using Debian, but I would install it in a heartbeat if the internet problem is fixed.

---

### Post by ddrichardson on 2009-04-24
And you say it works OK at college?

---

### Post by evermooingcow on 2009-04-24
Might be a MSS/MTU issue. Try doing this:  ```
sudo ifconfig eth0 mtu 1000
``` Where eth0 is your NIC.  Does that change anything? If not try again using 900, 800, etc. If you go low enough and it makes no difference then this is not the problem. If 1000 works try raising the value by 100 or so and keep going up until you find the upper limit.  1500 is default.

---

### Post by alcatraz on 2009-04-25
@mossman44: That are not too good news :( I love Ubuntu!
@ddrichardson: Yes, in the university it is working just fine!
@evermooingcow: Unfortunately that was not the problem. :( But thanks for trying.

If it really is not IPv6, it could be that here in the student house they are using a weird/broken gateway? Which produces partly broken packages? But that is far too unrealistic?

The problem itself remembers me to DNS problems. The weirdest thing is just, that pinging works. And when I load the website, it is downloading a part of it. e.g. the title. But for other websites it is working fine.
I also put the OpenDNS servers in my DNS list, but it does not make a difference.

It could also seem like only a speed problem. But some websites are super-quick. And others... almost not at all. So again back to DNS problem?

I just tried with the Knoppix Live CD. Something weird happened. It loads the websites which are not working on Ubuntu, BUT not entirely. For example for Facebook, Ubuntu only loads the Title. In Knoppix it also loads the header image. But not further!?

I was talking to the management of the building. One guy told me that MAYBE something was changed in the network. But he doesn't know anything about it. So I have to wait until monday until the "knowing" person comes to know if -and if yes, what- changed on the network.

Annoying this problem :(

---

### Post by ddrichardson on 2009-04-25
If it works on one network and not on another then it has to be something with the net in your building. I'd love to find out what...

---

### Post by alcatraz on 2009-04-25
OK, I am going to ask on Monday when the responsible guy is here again what they changed in their network.
But it is still weird that some things work and some don't... :(

---

### Post by alcatraz on 2009-04-25
Interesting: I tried to access the both websites which don't seem to work via lynx.

Facebook worked sometimes. It says "We're too cool to support your browser" :P 
When it does not work, it reaches HTTP/1.1 200 OK
and after a while it says this: Alert!: Unexpected server disconnect.

eBay (also not working on the other browsers works fine in lynx).
There must be a speed problem?

For me, it looks like there are some routers on the route not working.
But it's a week now. Someone would have fixed that!

---

### Post by evermooingcow on 2009-04-25
I would try running wireshark. It monitors all of your incomming/outgoing packets. Maybe you can see what going on.

---

### Post by alcatraz on 2009-04-26
Hey again guys,

@evermooingcow thank you very much for that tipp. That I hadn't that idea earlier is a miracle ;)

Anyway, I discovered some interesting stuff there.

It was something that I thought... they send -for what reason?- broken packages. But... why can Windows handle it?

Update:
By the way, I checked other websites: They also show checksum errors.
Also on Windows. So it really seem to be something wrong with the network here.

But still... why can Windows interpret those things?

Update:
I tried to disable the checksum offload:
> sudo ethtool --offload eth0 tx off
but the problem is still there.

---

### Post by Andbuntu on 2009-04-26
Hi,
 
It is interesting that it works fine elsewhere and that windows works ok where you are - this gives us something to compare/contrast against.  I would have a look at the windows settings in the failing location - check Internet_Options/Connections/LAN_settings (or the dial settings etc) and see what is there, eg a proxy setting.
 
It's about the only thing I can think of at the moment.
 
The TCP checksum offload is probably just your network adapter computing the checksum rather than CPU ... might be possible to disable this if it really is causing a problem.  [Check something like "sudo ethtool -k eth0" to get values to see if rx/tx checksumming on/off]
 
Hope that helps / cheers

---

### Post by alcatraz on 2009-04-26
I cannot find any setting which is different.
IP address, subnet mask, DNS address, gateway address ... everything fits to the windows configuration.
There are no proxy settings in Windows. It's set to "No proxy".

Disabling the checksum offload doesn't affect anything. The Wireshark outputs are the same and the websites are still not working.

Any other ideas? :(

---

### Post by alcatraz on 2009-04-28
I talked to the building manager and he told me that they replaced a router which gave wrong IP-addresses 1-2 weeks ago.

But that cannot be any problem!?
Unless the new router sends broken packages around?!

---

### Post by alcatraz on 2009-04-28
I tried another thing. Maybe that is helping to find out what is wrong:
> marc@tuxbook:~$ wget [http://www.facebook.com](http://www.facebook.com)
--2009-04-28 18:02:22--  [http://www.facebook.com/](http://www.facebook.com/)
Resolving [www.facebook.com](www.facebook.com)... 69.63.184.30
Connecting to [www.facebook.com|69.63.184.30|:80](www.facebook.com|69.63.184.30|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.facebook.com/common/browser.php](http://www.facebook.com/common/browser.php) [following]
--2009-04-28 18:02:23--  [http://www.facebook.com/common/browser.php](http://www.facebook.com/common/browser.php)
Connecting to [www.facebook.com|69.63.184.30|:80](www.facebook.com|69.63.184.30|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `browser.php.1'

    [        <=>                            ] 3,719       --.-K/s   in 6.7s    

**2009-04-28 18:02:31 (558 B/s) - Read error at byte 3719 (Connection reset by peer).Retrying.**


Any ideas? Pleeeeeeease, I'm desperate :(

---

### Post by nucleuskore on 2009-04-28
You'll just have to wait for this ipv6 thing to be resolved.

---

### Post by alcatraz on 2009-04-28
IPv6 doesn't seem to be the problem.

Because when I turn off IPv6 in Firefox, nothing changes.

---

### Post by nucleuskore on 2009-05-01
Try fixing the DNS manually to opendns
208.67.222.222
208.67.220.220

---

### Post by alcatraz on 2009-05-07
Already tried... no result :(

---

### Post by AnthraxMouthwash on 2009-05-07
Hi.  I am having this same problem, but only just recently.

I finally got wifi and internet working in Ubuntu Jaunty (using wicd for wifi connection instead of the standard-issue network manager).  One of the first things I did with my working web was install the ati accelerated gfx drivers.  They crashed Ubuntu on boot, so I removed them from the command line.  Fine.  But now my internet is acting very strange, and essentially doesn't work.  I am having the same issues as alcatraz (pretty much).


EXAMPLE...
Loading ubuntuforums.org takes a long time and only loads the page sometimes, but after that any page I visit spends a long time loading then gives me an error that says connection refused (not a timeout).

Google takes a long time to load, but usually does eventually load.  Attempting to do a search always fails and gives that connection refused error again.


HOWEVER...
If I load google, then intermittently disconnect my wifi and reconnect I can do a search, but after that any page I visit will again fail...  unless I disconnect and reconnect my wifi again inbetween every page, provided the page is a small one.


SO...
It seems that after connecting to my router I only get a small amount of web activity before I lose web... until I disconnect/reconnect to my router.


A FEW POINTS...
1.  My wifi is working fine (according to wicd).  Good strength on average.
2.  Package manager also has web issues and can not DL the package list.
3.  Disabling IPv6 in Firefox makes no difference.
4.  I have Win2k on the same machine.  Wifi, web and all work fine in Win2k.
5.  Web was working perfectly on Ubuntu Jaunty for a while before I stupidly
     installed (then removed) the ati gfx drivers.


SOME CURIOUS PERCULIARITIES...

If I ping ubuntu.com I get several successful pings.  If I do 5 pings, one of them is always very high.  This does not seem right to me... or perhaps it is?  IE, I will get four pings at about 20-25ms and one at 500-850ms, usually the third of the five.  I am not sure if it should be like this.

When I run iwconfig after booting (before doing anything), it tells me the bitrate is 5.5Mbit.  AFTER doing anything on the web (or trying to), iwconfig says the bitrate is 54Mbit.  Obviously 54Mbit is correct, but why does it begin at 5.5Mbit?  Strange?  Is there some way to force the initial connection to open at 54Mbit?

Sometimes my router shows up twice in wicd's connection dialogue, but is resolved when refreshing the list.  This does not seem to be a problem, though.

---

### Post by DJB1609 on 2009-05-07
> **alcatraz said:**
> Hello!

<snip>
Now the mysterious thing:
When I start in my Windows installation, it is working just fine!
I did install 9.04 today, still the same. My second notebook with 8.10 has the same problem.

What could that be? My only explaination is a kind of a protocol which can only be handled properly by Windows. But that is kind of impossible. Those things should be standardized.

<snip>
Marc

I use FF and thunderbird on XP, and ubuntu.

I had to stop using Ubuntu 8.1 because:

Errors:
Send/receive via thunderbird timed out.
Yahoo web-messenger could not connect to it's chat protocol (emails worked fine).
Various websites timed out far more than windows.
Cannot post to *any* forums - reading is OK.

I am now in XP, as my Jaunty install has the same problems as above. Exactly.

FF/Thunderbird all the latest available through updates.

XP all works. Ubuntu simply doesn't.

This is similar, very similar, to the OP's problems.

I am wireless on a Toshiba and an Asus eee1000H to an Asus W530G V2. 

All was well until I got the Asus, but two D-links failed, so I ended up with the Asus. When I had problems with wireless, I reinstalled 8.1 clean.

I gave up and waited. Now Jaunty is the same. So the 8.1 on the Toshiba and the Jaunty on the Asus eee have the same problems.

So, where can I start looking? Ipv6 makes no difference on or off in FF.

I think these may be relevant:
Send/receive emails times out.
Posting to any forums to edit/posts times out.
Yahoo can go into it's webmail, but not connect to it's chat service.
All was well before the Asus hardware.

I am a Linux novice, but can find my way around directories and the CLI. (Used to have an Amiga!)

DavidJ.

---

### Post by mossman44 on 2009-05-07
This internet problem is quite strange and annoying. What makes this even stranger is when I use Ubuntu 8.10 as a dual boot on my main hard drive, the internet has these issues but when I use it in a virtual machine in Virtualbox, these problems never occur and the internet works flawlessly. If it helps, I'm using Virtualbox 2.2.2 on a 32bit Windows Vista host and I am using the PCnet-FAST III (AM79C973) network adapter with NAT networking.

---

### Post by mossman44 on 2009-05-07
I just read disturbing news from a user named kabel who commented on a review of jaunty at [http://superphysics.awardspace.com/2009/04/25/ubuntu-904-review-desktop-emphasis-on-the-jaunty-jackalope/](http://superphysics.awardspace.com/2009/04/25/ubuntu-904-review-desktop-emphasis-on-the-jaunty-jackalope/)
According to kabel, ipv6 functionality is baked into the ubuntu kernel and can't be disabled. If ipv6 is indeed the cause of all of these problems, we may be in some trouble. Hopefully, Canonical will finally notice this or someone smart builds a kernel with ipv6 disabled by default.

---

### Post by DJB1609 on 2009-05-08
> **mossman44 said:**
> This internet problem is quite strange and annoying. 

It's a deal-breaker for me.

I have had to log into XP again to post this message.

I can log on to forums, just not post.

What's different about the connection when you post as opposed to just read? This could be a pointer to the problem.

DavidJ.

---

### Post by mossman44 on 2009-05-12
Come on guys we can't give up on this issue. If it isn't addressed, the fast paced progress and adoption Ubuntu has enjoyed may slow down significantly. We have good information here we just need someone to piece the puzzle together.

---

### Post by DJB1609 on 2009-05-13
OK. Now on eee1000H netbook remix, reformatted, fresh install.

Firefox as supplied, failed to post with original and OpenDNS servers.

Now trying "Quick Reply" option....

---

### Post by DJB1609 on 2009-05-13
> **DJB1609 said:**
> OK. Now on eee1000H netbook remix, reformatted, fresh install.

Firefox as supplied, failed to post with original and OpenDNS servers.

Now trying "Quick Reply" option....

Spoke too soon. Just so you guys don't hink I'm not trying, it's now 01:37 as I type - and that's after a reinstall!

It's a .php issue. I can't post any messages in Ubuntu on all flavours. 8.1, 9.04 and now 9.04 Netbook remix. 

I get: 

[http://lh4.ggpht.com/_wDh1GUxRIUA/Sgrl9XVEwXI/AAAAAAAABts/59w2Fxx-DvM/Screenshotcrop.png](http://lh4.ggpht.com/_wDh1GUxRIUA/Sgrl9XVEwXI/AAAAAAAABts/59w2Fxx-DvM/Screenshotcrop.png)

After a *very* long delay when posting here via quick-link or any other. 

I have cleared the firefox cache many times. 
This is a New install with *no addons*

I have tried 
[http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain](http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain)

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)


and many other sites and I know I am not alone.

I installed php from synaptic.........as mentioned in the above links.

Here's the php restart info from the terminal:
______________________________________________________
daje@daje-eee:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
daje@daje-eee:~$ sudo a2enmod php5
Module php5 already enabled
daje@daje-eee:~$ /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                          
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
daje@daje-eee:~$ sudo a2enmod php5
Module php5 already enabled
daje@daje-eee:~$ sudo /etc/init.d/apache2 restart 
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
daje@daje-eee:~$ 
_______________________________
This looks interesting:

httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down

followed by [fail]

Any ideas?

I'm trying.......but out of my depth. ](*,)

DavidJ.

---

### Post by DJB1609 on 2009-05-13
> **DJB1609 said:**
> 

I'm trying.......but out of my depth. ](*,)

DavidJ.

So, if this works it's from a clean install of Opera!

---

### Post by DJB1609 on 2009-05-14
> **DJB1609 said:**
> So, if this works it's from a clean install of Opera!

And if this works, maybe my problem is solved and we can chalk one up for Opera!

:popcorn: :p :p :p

DavidJ.

---

### Post by DJB1609 on 2009-05-14
Just to note, before I rush to work, that I can post to other groups as well!

Happy man! :)

I will update other threads later.

DavidJ.

---

### Post by DJB1609 on 2009-05-14
> **DJB1609 said:**
> Just to note, before I rush to work, that I can post to other groups as well!

Happy man! :)

I will update other threads later.

DavidJ.

Having problems on another thread..............maybe I spoke too soon. Sorry for the multiple posts, but I nned to see what's happening.

DavidJ.

OK. 
In Firefox - no change.
In Opera I can post, edit posts, use yahoo webmail, but it hangs on trying to edit my OP in "Advanced" edit. Any idea why?
(Not this Thread - it's not mine. This one: [http://ubuntuforums.org/showthread.php?t=1152896](http://ubuntuforums.org/showthread.php?t=1152896))

DavidJ.

---

### Post by DJB1609 on 2009-05-14
Sorry, given up on Ubuntu.

Will try another distro, and am downloading now.

So close, but no result.

Sorry, but surfing/posting should just work across three revisions of one distro on two machines - especially when MS - horrible though I find using it - just works.

Next - PCLInuxOS.

DavidJ.

---

### Post by mossman44 on 2009-05-14
> Sorry, but surfing/posting should just work across three revisions of one distro

If Canonical cannot figure this out, adoption of Ubuntu is going to slow significantly. I wish I could come up with a solution but I've searched deep into the forums, disabled certain services, changed my MTU size, installed several browsers including a stock copy of firefox, and tried every other trick in the book but all have failed.  Have any bug reports been filed for this problem?

More information that may help. I've only noticed these problems when using wired networking using ubuntu 8.10 and 9.04 while earlier versions never had these problems. Also, my laptop running Xubuntu 8.10 with a linksys wireless card never experiences these problems and the internet works smoothly. Wired networking has been around for a long time and an issue that is this annoying and has existed for this long is ridiculous. My suggestion is that everyone file bug reports and hope Canonical notices, or else Ubuntu is going to lose fans.

---

### Post by DJB1609 on 2009-05-14
> **mossman44 said:**
>  Have any bug reports been filed for this problem?



The couple I saw suggested it was a one-off for the poster, and they were closed. Perhaps Canonical assumed they were fixed, when the people, like me, just left Ubuntu.

I may issue a bug report. I guess these forums are filled with people with simple settings problems, and deeper issues get lost.

DavidJ.

---

### Post by alcatraz on 2009-05-21
I finally got it working!

I found a hint on another ubuntuforums.org thread: [http://ubuntuforums.org/showthread.php?t=430855](http://ubuntuforums.org/showthread.php?t=430855)

> Basically, you can try writing in a root terminal:
Code:

```
echo "4096 16384 131072" > /proc/sys/net/ipv4/tcp_wmem
echo "4096 87380 174760" > /proc/sys/net/ipv4/tcp_rmem
```

If that solves the problem, you can make the changes permanent, adding the following to /etc/sysctl.conf :
Code:

```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

The last value (kernel maximum TCP send buffer space) was set way too high. I assume that the new router installed in my building is improperly configured... It should normally be able to handle...

---

### Post by DJB1609 on 2009-05-22
> **alcatraz said:**
> I finally got it working!

I found a hint on another ubuntuforums.org thread: [http://ubuntuforums.org/showthread.php?t=430855](http://ubuntuforums.org/showthread.php?t=430855)



The last value (kernel maximum TCP send buffer space) was set way too high. I assume that the new router installed in my building is improperly configured... It should normally be able to handle...

Well, not in Firefox - so this is Opera!

---

### Post by DJB1609 on 2009-05-22
Well! 

So far so good. I can quote a reply, edit that quote and now this post from Quick Link.

None of this works in Firefox!

DavidJ.

[Edit] OK. Hooray for Opera :popcorn:

Why this doesn't work in FF I don't know.

I'm just happy to be posting. Thanks for the info.

I will monitor the next few days and report back.:) 
Thanks Alcatraz - I will get my Chinese friend to have the ISP look at the routers in the building.
Still not working in Firefox, though! - I get the "Open or save 'editpost.php' error"

DavidJ.

---

### Post by DJB1609 on 2009-05-24
> **DJB1609 said:**
> 

I will monitor the next few days and report back.:) 

DavidJ.

](*,)

I spoke too soon. Now I am back to square one, with no mods to the system.

The engineers came, said settings were ok. Saw it working in XP and Vista and told me to use that!

I can't issue a bug report, as I wouldn't know what to say. To be honest I am amazed at the lack of interest in this problem. I see other threads and people are told:

"Post the output of this"
"Load this and post the log"
"sudo gedit xxx and enter yyy"

Here, with this problem, it seems there is a resounding silence, and that's probably why there are no answers. Nobody knows, or cares as it's not a "typical" problem.

Sorry, but after so many hours, reinstalls and investment in new hardware, I've followed my wife back to Windows. I don't think I can be accused of not trying with Linux. Shame. :-({|=

DavidJ.

---

### Post by ddrichardson on 2009-05-24
While I appreciate your frustration, you have appended to someone else's thread - that's why you haven't got much of a response.  People looking over the forum will see a thread with several replies and assume it was answered, especially if there has been no activity recently.

I only see this thread because I've answered the OP and am still subscribed to it, having been away for a while - I'd have been glad to offer you more assistance but wish you all the best.

---

### Post by DJB1609 on 2009-05-24
> **ddrichardson said:**
> While I appreciate your frustration, you have appended to someone else's thread...

Hi, and thanks for the response.

II thought joining a thread with the same/very similar problem was the way to go.

I am not giving up, despite wanting to throw the bloody computers out of the window. I really dislike Microsoft and Windows, and tell everyone about Linux as much as possible.

I have a new thread: 
[http://ubuntuforums.org/showthread.php?p=7336602#post7336602](http://ubuntuforums.org/showthread.php?p=7336602#post7336602)


> **ddrichardson said:**
> 
I'd have been glad to offer you more assistance but wish you all the best.

If you can see through the frustration, then any help would be much appreciated.

Thanks,

David. 
(Still trying.)

---

### Post by ddrichardson on 2009-05-24
> **DJB1609 said:**
> If you can see through the frustration, then any help would be much appreciated.

Thanks,

David. 
(Still trying.)
I've replied in your new thread.

---

