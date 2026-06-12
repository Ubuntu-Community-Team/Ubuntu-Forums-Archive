---
title: "remote access"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by amalafrida on 2011-11-28
I've succeeded in getting the LAMP ensemble set up on my local machine. Everything works fine. I can serve web pages to any box on the LAN.

The part that is driving me crazy is remote connection.

In order to keep this as simple as possible, I've pulled the router out of the loop.

Numbers look like this:
HOST: xxx.xxx.xxx.xxx -->
browser serves correct web page;
google translate: fails, of course (invalid url)

MODEM: xxx.xxx.xxx.xxx -->
browser serves modem config/info page;
google translate: fails (invalid url)

INTERNET IP ADDRESS, static address assigned by ATT: xx.xxx.xxx.xxx -->
from my computer (xxx.xxx.xxx.xxx) browser serves modem config/info page;
from remote computer browser: timeout
google translate: fail

INTERNET GATEWAY ADDRESS: xxx.xxx.xxx.xxx -->
browser yields 'time out';
google translate: fail

all four addresses ping out nicely.

How in the world do I get remote access to this machine? I've floated around chat rooms and spent well over an hour with BellSouth ... any suggestions?

Thanks in advance.

Robert

Solution: after much back-and-forth with ATT (modem replacement, multiple config changes, etc.) it turns out that only one tiny config switch needed to be thrown, to wit:
Advanced Configuration of the modem contains "Let LAN device share internet address?" Two choices: No, use private IP address / Yes, use public IP address." Selected "Yes." and it works fine. Apparently, this is the IP passthrough option.

So, the bottom line is this: public IP address must ping out before any remote connection is possible. Solve that problem. That's the first step. After that, port on router (e.g. 22 for ssh) must be forwarded.

All works swimmingly now.

Thanks to all for the help, especially drdos2006.

---

### Post by stephenbbb on 2011-11-28
same issue here:

I have Bell as ISP and cannot access the server from outside. spent maybe 5 hours with customer service all in vain:

they DO NOT support ssh etc.

Gurus please, help.

---

### Post by amalafrida on 2011-11-29
I will definitely contact BellSouth and confirm that. If that is the case, I'll begin looking for another ISP.

Thanks for your response.

Robert

---

### Post by stephenbbb on 2011-11-29
Robert,

are you willing to try to ssh to my box just for testing? I can send you details in a private message if this forum supports that.
I have no access to any tools outside my house as the company has a very restrictive firewall and I cannot do any testing. let me know if I can do sth to help you.

regards
stephen

---

### Post by amalafrida on 2011-11-29
yes, absolutely would like to try. let's get together off-list and try it both ways.

my e-mail: [email]mullinrobert@gmail.com[/email]

thanks.

robert

---

### Post by amalafrida on 2011-11-29
Just spoke with BellSouth. They responded that they definitely do not discourage nor inhibit ssh remote-in. That it is technically feasible. Although they would not help me arrange the setup, they offered to get me in touch with a $49/hour service that would arrange it for me.

So back to the numbers. How does one do this?

---

### Post by drdos2006 on 2011-11-29
I just came across your post and am suprised that no one else has offered a response. 

1. I pinged your ISP ok, but could not ping your IP address.
Check the internals of your modem, see if you can turn on "Respond to Ping on Internet Port" for the moment. You can turn it off later.

2. you should not publicly advertise your static WAN address, please remove it from your post.

3. Connect to [http://www.whatismyip.com/](http://www.whatismyip.com/) and answer yes, you have the correct IP address in your post. If not please PM me your IP address.

4.Remove your static IP from your post.

Once I can ping your modem, then it is a matter of port forwarding your SSH port to your internal computer IP address (192.168.1.64) 

regards

---

### Post by amalafrida on 2011-11-29
Thanks for the response. I edited the previous post and removed the ip addresses.

I set router (not modem) to "respond to ping on internet port"

whatismyip.com responds correctly.

should I pull the router out of the loop? However, I see nothing in the modem config that would permit me to "respond to ping on internet port".

Robert

---

### Post by drdos2006 on 2011-11-29
No need to disconnect router, you need to allow modem to receive ping from Internet instead.

I am away for an hour or two. Will be back later.

regards

---

### Post by deonis on 2011-11-29
Do you have root access to the server you are trying to have the ssh connection to? If yes, then you can make your server listen on the HTTPS port 443. Add  Listen 443
to /etc/ssh/sshd_config.  And then you can use ssh from your desktop  ssh -p 443 myserverIP

---

### Post by drdos2006 on 2011-11-29
I still cannot ping to your modem's IP address and get a response.
Is there a setting in your modem to allow the modem to receive a ping from the Internet ?

regards
[edit]
What is the brand and model of your modem ?
[/edit]

---

### Post by amalafrida on 2011-11-29
modem config page provides no "respond to ping on internet port"

I do have root access. Have added Listen 443 to /etc/sshd_config.

and restarted ssh service.

I have always been able to ssh back and forth on the LAN. It's getting in from remote that is the problem.

Hope I've understood directives correctly.

$ssh -p 443 xxx.xxx.xxx.xxx (my static ISP address) times out.

Thanks.

Robert

---

### Post by drdos2006 on 2011-11-29
From a terminal type this, change the  internal.lan.ip.address to the address of the machine you are trying to connect to and your username.
See if it works on your lan.

  ssh [email]username@internal.lan.ip.addres[/email]s  -X

regards

---

### Post by deonis on 2011-11-29
I don't get that, can you use local ssh login on your server  (ssh 127.0.0.1)? Also, can you try to ssh to my server ssh dsn.yips.ca, you should see connection prompt. Let me know if you see anything...

cheers

---

### Post by amalafrida on 2011-11-29
ssh 127.0.0.1 ... ssh: connect to host 127.0.0.1 port 22: Connection refused
ssh dsn.yips.ca ... yes, connect and to login prompt
Modem Name ProLine
Model 	F90-610025-06

sshd_config Listen 22
ssh_config Port 22

changed sshd_config "Listen" to "Port"
now ssh 127.0.0.1 works fine

---

### Post by drdos2006 on 2011-11-29
It appears that ssh is not working.
ssh 127.0.0.1 ... ssh: connect to host 127.0.0.1 port 22: Connection refused

Go to System -> Administration -> Synaptic Package Manager and install ssh ( both server and client )

then from a terminal try ssh 127.0.0.1

regards

---

### Post by amalafrida on 2011-11-29
yes, I just edited previous post. ssh 127.0.0.1 is working fine.

thanks.

robert

---

### Post by drdos2006 on 2011-11-29
Ok.

type "ifconfig" to get the internal LAN IP address,
open your modem and port forward port 22 to your internal LAN IP address computer. Then I shall try to connect to yoour WAN IP address.

regards
[edit]
the protocol is TCP
[/edit]

---

### Post by amalafrida on 2011-11-30
my modem config page provides no means to forward port 22.

I've looked and looked at the "configure connection" page. just not there. is it possible that I have a down-and-dirty modem and must upgrade?

The only config item that is remotely related is two radio buttons that permit this:
[quote]"A very limited number of applications require that the public IP address assigned to the modem be used by the local LAN device.
Let LAN device share Internet address?

No, use private IP address.


Yes, use public IP address. [end quote]

On the other hand, my router config page does provide "port forwarding" options.

Down near the bottom of this page, a screenshot of my modem configuration page is to be found--> [http://www.broadbandreports.com/forum/r22499716-Modem-westall-modem-model-F9061002506-port-forwarding-issue?hifilter=](http://www.broadbandreports.com/forum/r22499716-Modem-westall-modem-model-F9061002506-port-forwarding-issue?hifilter=)

r.

---

### Post by drdos2006 on 2011-11-30
Give me five minutes to check out the modem specs.

regards

---

### Post by drdos2006 on 2011-11-30
Ok, looks like some people have issues and some don't with this model. ( F90-610025-06 )  I am assuming it the single port modem and you need to port forward 22/TCP in your router.

regards
[edit]
More information

[http://forums.att.com/t5/Routers-and-Home-Networks/Bridge-Mode-for-F90-Modem-to-Linsys-Router/td-p/2027807](http://forums.att.com/t5/Routers-and-Home-Networks/Bridge-Mode-for-F90-Modem-to-Linsys-Router/td-p/2027807)
This section here may help you to put the modem into bridged mode to the router.

Re: Bridge Mode for F90 Modem to Linsys Router
Options

    * Mark as New
    * Bookmark
    * Subscribe
    *
    * Subscribe to RSS Feed
    *
    * Highlight
    * Print
    * Email to a Friend
    *
    * Report Inappropriate Content

03-29-2010 03:11:47 PM

Hello marhar,

 

Thank you for the reply.

If you are not getting the same options, please try to steps for Westell F90 modem.To bridge the Westell F90 modem, do the following:

   1. Open a web browser.
   2. Type 192.168.1.254 in the address bar.
   3. Click the Go button or press the enter key on the keyboard.
   4. Click the Advanced link.

      There may be a prompt for a Modem Access Code. If so, do the following:
   5. Locate the yellow sticker on the bottom of the Westell F90 modem.

   6. Type the code in the Modem Access Code field.
   7. Click the Continue button.

   8. Click on the PPP Location link.
   9. Choose PPP is on the computer, gateway or router radio button.
  10. Click the Save Changes button. 

[/edit]

regards

---

### Post by amalafrida on 2011-11-30
placing machine in 'bridged mode' as per instructions cuts all internet connectivity. I am forced to reset the modem in order to regain connectivity.

thanks, but just did not work.

I can successfully ping public ip from LAN, but not from a remote site. Any thoughts? Any further suggestions?

I certainly appreciate your attention to this matter. Quite a tough nut to crack.

traceroute from LAN to public IP (successful):
traceroute my.public.ip.address
traceroute to 74.181.252.241 (my.public.ip.address), 30 hops max, 60 byte packets
 1  10.0.0.1 (10.0.0.1)  1.021 ms  1.264 ms  1.879 ms ... bing, hits the router
 2  adsl-074-181-252-241.sip.mem.bellsouth.net (my.public.ip.address)  10.651 ms  18.783 ms  19.076 ms ... bing, hits the modem NIC

traceroute from remote site to public ip address:
traceroute my.public.ip.address (fails)
traceroute to my.public.ip.address (my.public.ip.address), 30 hops max, 60 byte packets
 1  hdo127lab190.reggie.first.lib.ms.us (172.31.127.33)  4.746 ms  4.885 ms  87.057 ms
 2  172.31.127.1 (172.31.127.1)  8.326 ms  23.399 ms *
 3  172.17.209.1 (172.17.209.1)  87.437 ms  89.156 ms  89.788 ms
 4  12.81.52.26 (12.81.52.26)  187.721 ms  187.847 ms  188.341 ms
 5  12.81.104.92 (12.81.104.92)  89.834 ms  187.219 ms  187.450 ms
 6  * * *
 7  172.17.209.227 (172.17.209.227)  20.305 ms  86.711 ms  86.825 ms
 8  * 74.231.173.5 (74.231.173.5)  89.997 ms  90.101 ms
 9  12.81.48.6 (12.81.48.6)  21.835 ms  87.577 ms  88.676 ms
10  ixc00mem-7-0-1.bellsouth.net (65.83.237.77)  37.160 ms  110.459 ms  110.608 ms
11  * 12.81.52.47 (12.81.52.47)  95.265 ms  95.369 ms
12  * 12.81.52.24 (12.81.52.24)  18.241 ms  18.387 ms
13  12.81.52.21 (12.81.52.21)  17.503 ms  103.237 ms  103.410 ms
14  70.159.236.104 (70.159.236.104)  18.666 ms  103.542 ms  103.727 ms
15  70.159.236.35 (70.159.236.35)  18.296 ms  102.205 ms  102.707 ms
16  * * *
17  * * *
29  * * *
30  * * *
never reaches destination

Robert

---

### Post by drdos2006 on 2011-11-30
From the link I gave you, it appears that this modem is full of problems. Have a look at the last post from dggriffin.

My suggestion at this time would be to replace the modem and router with a modem/router that will allow you to port forward. See if you can beg, borrow one from a friend to test with.

regards

---

### Post by amalafrida on 2011-11-30
yep. i think you're on to something. I did read the post. currently on line with ATT tech support, trying patiently to walk them through a simple ping to my public ip to establish that likely the problem is on their end.

we'll see.

will get back with you directly.

Robert

---

### Post by amalafrida on 2011-11-30
Ok. Long conversation with ATT. After much ado, they say that they can ping my public IP. I've tried it twice offsite today with no success. I wonder if I might get you to give it a try.

At least, if now the public IP is visible, as it has not been heretofore, I'll be able to move forward to establishing an ssh session.

If you cannot ping it, then I'll begin searching for a replacement modem

Thanks in advance,

Robert

---

### Post by amalafrida on 2011-11-30
so, just trying to get things in order here.
am i correct in assuming that pinging that public address is the sine qua non of setting up this connection?

if that does not work, then nothing can move forward?

kind of like a telephone analogy ... if no one answers the number you dial, then conversation is impossible. am I seeing this correctly?

robert

---

### Post by drdos2006 on 2011-11-30
Hi Robert

I tried to ping your public address but cannot get a response. Some modem allow the ping to be received in the settings section. If ATT have said they can ping your modem then they might be using different terminology to say they can connect to your modem. 

Yes, you are correct using the telephone analogy.

My advice would be to get a modem/router where you can tweak the settings.

regards

---

### Post by amalafrida on 2011-11-30
yes, thanks for the response. i've located a combo modem/router in Memphis and will run up tomorrow and snag it. Leaving town soon and will probably not be able to get back on this for 5 or 6 days.

the seller is an ex-ATT tech/installer. he seems to think this will work. and has offered to take it back if it does not.

AT&T 2Wire Modem 2701HG-B - $35 (Bartlett)
Up for sale is one AT&T 2Wire 2701HG-B Modem with ac adapter & ethernet cable, not included cdrom, telephone cables, or manual.

And once again thanks for you help. I don't really understand why ubuntu people lock in on an issue like this and make an effort to get it taken care of, but that's just another reason why I turned away from Microflaccid 7 years ago and have never looked back. I must confess that I've taken far more from the Ubuntu community than I have returned. But after this, I'm gonna change my ways.

All the best.

---

### Post by drdos2006 on 2011-11-30
No problem.
I have bookmarked your topic and will check back in 5 or 6 days (unless you want to PM me when you are ready ).

regards

---

### Post by stephenbbb on 2011-12-01
Robert was unable to ping my IP.
when I go in advanced settings I have:
                                                                                                                       ATM Circuit Identifier:                                 VPI:                                 0
                                                                                                                                     
                                VCI:                                 35
                                                                                                                                                                                                                                      ATM Encapsulation:                                                                                                                                                                                                                                                                                            bridged LLC
                                                                                              ATM PVC Search:                                                                                                                                      Disabled

in application support/advanced I discovered that there was 'block ping' checked. it is now unchecked.
Robert, please, try pinging again.

BTW ssh will not work as my Ubuntu is totally frozen and I am posting this from windows, which does not have an ssh server.
drdos,
pls advise if I need to change some of the settings above.
thank you all. I really wish Bell could hire smb who understands networking.

---

### Post by amalafrida on 2011-12-01
Stephenbbb:
ping succeeds to your public ip.
felicitations!

just off the line with ATT for the 20th time. they've told me continuously that yes, your public IP can be pinged. Spoke to a former ATT tech and he explained that for a technical issue of this sort I'd need to get past the "Tier-1 talkers" and on to a Tier-2 technician. And yes, I did.  I explained that ping just did not work. I asked if they had actually sat down at a command line and run ping on the address. Answer: "no, but we have our test equipment that verified the address." So, then, might you please just actually PING the number ... after much waiting and back-and-forthing, they reported that indeed, ping and traceroute were negative. I am now officially enrolled with a trouble ticket number.

Thanks folks for all the help and patience. Perhaps there is light at the end of this ssh tunnel. I'm to give them 24-72 hours to resolve the issue. We shall see.

---

### Post by stephenbbb on 2011-12-01
Robert, 

did u try the advanced network settings on the modem setup? probably there is a check box 'block ping' somewhere.

DrDos,

please, advise how to forward the ssh from the modem to a box using the 192.168.2.x private/internal IP?

thanks a lot and again, this is Bell's job, but they don't care.

PS. I had decided to drop them and started with a cable ISP, tested magicjack and called Bell to cancel. their customer loyalty department gave me phone and fibe internet for $34, so I decided to drop the cable and enjoy a real phone line.

---

### Post by drdos2006 on 2011-12-01
Hi there.

You need to forward the port 22 in your router to the IP address of the computer attached to your router.

Check out [http://portforward.com](http://portforward.com)  for more info on your modem/router model.

You will probably have to allow your firewall to accept the incoming port number as well as port forwarding.

regards

---

### Post by drdos2006 on 2011-12-01
Hi Robert

I am now able to ping your IP address.

regards

---

### Post by amalafrida on 2011-12-01
jumpin' jesus, merci beaucoup! now I can move ahead. Att ... what a group. I think I'll phone tomorrow and attempt to get a diagnostic read-out about this business.

In any case, after this is cleared up, I'm going to go back and make a resume of our work and post it 'ubuntu somewhere' so that perhaps others will be able to follow a clear path to getting this sort of thing done.

Clearly, at least in our case, a ping to the public ip is the key (or as the attorneys would have it ... 'the sine qua non') to the kingdom.

Thanks again to all for having worked with me on this.

It ain't over yet, so I'll probably be back at you until I can establish an ssh tunnel into my local machine. But for now, As Richard Farina said: "been down so long looks like up to me."

robert

---

### Post by drdos2006 on 2011-12-01
That is good news.

Are you able to log in to your router and port forward to your computer LAN IP address ?

regards

---

### Post by amalafrida on 2011-12-02
Still ain't there.
canyouseeme.org on my public ip ports 22 and 80 ... timed out!
Both ports are forwarded in router config.
But you get a good ping?

still confused.

r.

---

### Post by drdos2006 on 2011-12-02
Hi Robert

I can ping your IP but I cannot ssh your IP.

 ping xx.xx.xx.xx
PING xx.xx.xx.xx (xx.xx.xx.xx) 56(84) bytes of data.
64 bytes from xx.xx.xx.xx: icmp_seq=1 ttl=236 time=268 ms
64 bytes from xx.xx.xx.xx: icmp_seq=2 ttl=236 time=268 ms
64 bytes from xx.xx.xx.xx: icmp_seq=3 ttl=236 time=268 ms
64 bytes from xx.xx.xx.xx: icmp_seq=4 ttl=236 time=269 ms
64 bytes from xx.xx.xx.xx: icmp_seq=5 ttl=236 time=269 ms
64 bytes from xx.xx.xx.xx: icmp_seq=6 ttl=236 time=269 ms

What model router do you have ?

regards

---

### Post by amalafrida on 2011-12-02
current router:
Modem Name ProLine
Model F90-610025-06

but when I return home will install:
ATT's 2Wire 2701HG-B

Spoke to ATT this morning and they say the problem is not yet fixed, but they are working on it. So the situation could be changing from moment to moment.

This morning I tried these diagnostics:
data recorded 12/02/2011
$ telnet xxx.xxx.xxx.xxx
Trying xxx.xxx.xxx.xxx...
telnet: Unable to connect to remote host: Connection timed out


$ traceroute xxx.xxx.xxx.xxx
traceroute to xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx), 30 hops max, 60 byte packets
 1  hdo127lab190.reggie.first.lib.ms.us (172.31.127.33)  52.806 ms  155.312 ms  159.032 ms
 2  172.31.127.1 (172.31.127.1)  654.277 ms  668.207 ms  770.353 ms
 3  172.17.209.1 (172.17.209.1)  872.971 ms  873.803 ms  1075.990 ms
 4  12.81.52.26 (12.81.52.26)  1077.020 ms  1080.390 ms  1081.730 ms
 5  12.81.104.92 (12.81.104.92)  1096.113 ms  1100.372 ms  1104.181 ms
 6  * * *
 7  * 172.17.209.227 (172.17.209.227)  1560.531 ms  1560.928 ms
 8  * * *
 9  12.81.48.6 (12.81.48.6)  1661.638 ms  1722.810 ms  1723.044 ms
10  ixc00mem-7-0-1.bellsouth.net (65.83.237.77)  1698.870 ms * *
11  * 12.81.52.47 (12.81.52.47)  7638.684 ms *
12  * 12.81.52.24 (12.81.52.24)  1715.281 ms  1853.639 ms
13  * 12.81.52.21 (12.81.52.21)  1928.756 ms *
14  70.159.236.104 (70.159.236.104)  1962.519 ms *  2421.045 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


$ ssh xxx.xxx.xxx.xxx
ssh: connect to host xxx.xxx.xxx.xxx port 22: Connection timed out


$ ping xxx.xxx.xxx.xxx
PING xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) 56(84) bytes of data.
--- xxx.xxx.xxx.xxx ping statistics ---
180 packets transmitted, 0 received, 100% packet loss, time 180369ms

---

### Post by drdos2006 on 2011-12-02
If I can ping your IP address then all that needs to happen now is to port forward in the router.

I installed a server through Virtualbox, installed ssh on the server with:
sudo apt-get install ssh
I port forwarded to the server IP in the router,  from my desktop terminal I ran: ssh [email]vm-server70@xx.xx.xx.xx[/email] and it informed me that the key had been changed. So I went to my .ssh hidden directory, opened up the "known_hosts" file, deleted everything in there, ssh again, accepted the new ssh-key, entered the password and all is good. I am connected

What router do you have connected at the moment or are you out of town and unable to access the router ?
[edit]
I see you have the modem F90-610025-06 but I do know which router you have connected to the modem.
[/edit]

regards

---

### Post by amalafrida on 2011-12-02
same old router/modem combo. i've decided to leave it in until ATT says they have their work done. then I'll get the new one in.
My current router is Netgear WGR-614 and I have forwarded ports 22 & 80 on it.

Leaving town here in an hour or so. Won't be able to get much else done until Monday. But while I'm out I'm going to leave this box up and running so that I can do some remote pecking at it while on the road.

r.

---

### Post by drdos2006 on 2011-12-02
OK, no problem. Shall wait till then.

regards

---

### Post by amalafrida on 2011-12-04
Ok. Back in pocket. Tell me what you get from Queensland on ping. I'm told from other sources, same ole same ole ... 'time out'.

Thanks in advance.

Robert

---

### Post by drdos2006 on 2011-12-04
Hi Robert

I can ping your IP but I cannot ssh your IP.

ping xx.xx.xx.xx
PING xx.xx.xx.xx (xx.xx.xx.xx) 56(84) bytes of data.
64 bytes from xx.xx.xx.xx: icmp_seq=1 ttl=236 time=268 ms
64 bytes from xx.xx.xx.xx: icmp_seq=2 ttl=236 time=268 ms
64 bytes from xx.xx.xx.xx: icmp_seq=3 ttl=236 time=268 ms
64 bytes from xx.xx.xx.xx: icmp_seq=4 ttl=236 time=269 ms
64 bytes from xx.xx.xx.xx: icmp_seq=5 ttl=236 time=269 ms
64 bytes from xx.xx.xx.xx: icmp_seq=6 ttl=236 time=269 ms

It appears you might have to access your Netgear WGR-614. Follow the prompts in portforward.com for your model.

[http://portforward.com/english/routers/port_forwarding/Netgear/WGR614/SSH.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WGR614/SSH.htm)

regards
[edit]

Just reread my email. The IP addresses I have are from stephenbb.....:(
Please PM your IP address. I can ping stephenbb not SSH but I do not have your IP address.
[/edit]

---

### Post by drdos2006 on 2011-12-04
Ok, I found your IP address. Still timimg out.

regards

---

### Post by amalafrida on 2011-12-04
ok. thanks. back on the phone with ATT tomorrow. will return.

r.

---

### Post by amalafrida on 2011-12-06
drdos2006,

now then, back on the line with ATT this morning. still no resolution. they say the ping and traceroute are timing-out at the modem.

solution: send me a new modem. will arrive tomorrow. will then configure in conjunction with Tier-2 tech support and possibly (unlikely!) resolve the problem.

Again, thanks for your patience and tenacity in seeing me through this matter. I understand that this is NOT strictly an Ubuntu problem and that your help is above and beyond the call of duty and quite outside the real purpose of ubuntuforums.org.

Cordially,

Robert

---

### Post by drdos2006 on 2011-12-06
No problem.
To help each other is in the spirit of Ubuntu.
I hope a new modem resolves the issue.

regards

---

### Post by stephenbbb on 2011-12-15
Success:

I was able to ssh to my desktop at home today from my laptop sitting at a Starbucks downtown Toronto. based on the instructions in portforward I added a new application and forwarded 22 and also enabled SSH server, which is showing in the list of applications I can enable in the router. one of them worked ;-)
now I have to secure the box disabling read access to any dir above the guest home dir.

---

