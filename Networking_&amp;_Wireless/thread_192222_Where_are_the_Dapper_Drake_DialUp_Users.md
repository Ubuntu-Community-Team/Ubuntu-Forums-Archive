---
title: "Where are the Dapper Drake DialUp Users?"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by bigfinch4991 on 2006-06-08
It seems everyone these days has some kind of fast internet, but some people still use dialup to connect. I had an external serial modem and used WV Dialer to connect to my ISP using Breezy. I did a clean install of Dapper Drake, but the the setup that I had previously done with WV Dial conf and such has [COLOR="Sienna"]stopped working.[/COLOR] I searched these forums for advice and have found that very few postings came from the Dapper Drake side of the pond. No one seems to be worrying about dialup. If [COLOR="DeepSkyBlue"]ANYONE[/COLOR] has successfully connected to their ISP or just to the internet at all using Dapper Drake and dialup, [COLOR="SandyBrown"]PLEASE[/COLOR] reply to this thread. I hope this will enable people like me who are frustrated with the lack of response to find the answers they seek. All we need is one or two success stories and how they pulled them off to solve our problems. ANY information at all is greatly appreciated. Don't give up my dialup friends!

---

### Post by zxee on 2006-06-08
Actually there are several posts/threads here in dapper about dial up not working. I know because I've responded to some of them-so do a search on my name if you want to look at them. The short story is that dial up and it seems other means of accessing the internet in dapper has problems. Using pppconfig as root from a shell and modem monitor (an applet you can add to your panel) gets me connected. I recommend that you provide a detailed output of what's happening when you attempt to connect if you're using pon or wvdial copy and paste the output from those tools or start gnome-ppp from a shell/terminal and provide the output of that. I have filed a bug about dial up in dapper. Perhaps it would help to have more people letting developers know there are problems. Which means posting in the developer section or irc or? Hope that helps.
BTW I don't mean to suggest that modem monitor is the answer. It works sometimes but if the connection drops or fails to connect then I have found I need to delete modem monitor, re-start the computer, create a new modem monitor and try to re-connect. Also gnome-ppp which worked well in breezy does not work in dapper.

---

### Post by gray-squirrel on 2006-06-09
I've been able to use dial-up from the beginning, even with previous editions of Ubuntu and Kubuntu.  However, I've never been able to connect successfully with a GUI application except through Modem Lights (which apparently has disappeared).  I'm going to try out a few other possible solutions before I post or file a bug report, because I may have overlooked something.

For right now, though, setting up a connection via [FONT="Courier New"]sudo pppconfig[/FONT] and dialing with [FONT="Courier New"]sudo pon[/FONT] works well for me.  I terminate the connection with [FONT="Courier New"]sudo poff[/FONT].

It would be nice, though, to be able to dial with a GUI application, because I can monitor the traffic and can also tell when my connection is about to get dropped.

---

### Post by bigfinch4991 on 2006-06-09
Well here's some more information. I enter the coes to configure wvdial. It scans my ports and then puts out: 
Sorry, no modem was detected! Is it in use by another program? Did you configure it properly with setserial? 

Please read the FAQ at [http://open.nit.ca/wiki/?Wvdial](http://open.nit.ca/wiki/?Wvdial)

-------------
I tried pppconfig to set up my Earthlink account. It's so confusing. Especiall the static/dynamic wierd stuff.

---

### Post by zxee on 2006-06-09
[QUOTE=gray-squirrel]I've been able to use dial-up from the beginning, even with previous editions of Ubuntu and Kubuntu.  However, I've never been able to connect successfully with a GUI application except through Modem Lights (which apparently has disappeared).  I'm going to try out a few other possible solutions before I post or file a bug report, because I may have overlooked something.

For right now, though, setting up a connection via [FONT="Courier New"]sudo pppconfig[/FONT] and dialing with [FONT="Courier New"]sudo pon[/FONT] works well for me.  I terminate the connection with [FONT="Courier New"]sudo poff[/FONT].

It would be nice, though, to be able to dial with a GUI application, because I can monitor the traffic and can also tell when my connection is about to get dropped.[/QUOTE]

Never huh? Well gnome-ppp does work well for me in breezy. There seem to be more & more distros that don't bother with dial up support. I multi-boot a few differnt distros and have had to put together ppp on a couple of those. I think that chestnut-dialer [http://www.icewalkers.com/Linux/Software/519200/chestnut-dialer.html](http://www.icewalkers.com/Linux/Software/519200/chestnut-dialer.html)  or [http://prdownloads.sourceforge.net/chestnut-dialer/chestnut-dialer-0.3.2.tar.bz2?use_mirror=umn](http://prdownloads.sourceforge.net/chestnut-dialer/chestnut-dialer-0.3.2.tar.bz2?use_mirror=umn)
could work for you although I haven't tried it on debian based systems. 
I hope that us dial up users can get the attention of the ubuntu developers.

---

### Post by woodtw on 2006-06-11
Bump, bump, bumppty, bump, bump!

---

### Post by Patb on 2006-06-11
Well I am also one of the seeming few who use dialup with Dapper.  I have an external hardware modem which Dapper failed to autodetect (Breezy found it okay).  I have found that pppconfig seems to work okay to set up a connection but one problem I have not been able to overcome is that Dapper will always dial my ISP at startup.  What program is actually initiating this connection at startup, I have no idea.  Any suggestions on how to find out would be welcome.  

In Breezy, I had things working quite well.  Even down to dialling on demand using the 'demand' option in pppd but that seems not to work in Dapper - inserting the 'demand' option into the /etc/ppp/options file just stops pppd from dialling altogether.  Trying to set up diald to automatically bring up the link when required does not seem to get me anywhere.  Overall, setting up a dialup connection seems a bit more complicated and unsatisfactory than it should be.   

Cheers, Pat.

---

### Post by dspiteri on 2006-06-11
These are my observations about Dapper dialup PPP:

The networking preferences create a pppd provider called ppp0 which can be manually invoked with 'pon ppp0' or 'ifup ppp0'.

When ppp0 is activated from networking preferences, it effectively runs 'ifup ppp0' which requires root access, thus requiring sudo and password. Same for the modem-applet, which is not good usability. Using pon only requires 'dip' group access.

When ppp0 is activated, it is automatically bought up on boot from /etc/network/interfaces, which is the correct behaviour for ifup but not necessarily the desired behaviour for dialup.

The gnome-ppp app uses wvdial, which for some reason is currently broken using dapper with a standard serial modem.

modem-applet runs a perl network autoconfigurator which eats up a non-trivial amount of CPU time, and is also ugly.

The method which I implemented was to create two application launchers: one called online, the other disconnect. Online runs '/usr/bin/pon ppp0' and disconnect '/usr/bin/poff'.  For usability I arbitrarily assigned green and red icons respectively.

My mother can now change the ppp configuration in network preferences and this will be used in the pon/poff method. Just be sure that ppp0 is enabled, but don't activate it.

---

### Post by xoros on 2006-06-12
I have dialup working in Dapper.  
First get the latest sl-modem-daemon package
Next sudo dpkg -i sl-modem-daemon*.deb
If that went good it automatically sets up a symlink
Finally,
Using wvdial,  make sure you have /etc/wvdial.conf set up correct.  
I had to put in:
Carrier Check = no
Modem Type = Analog Modem
and check this line: Modem = /dev/modem  (make sure modem is whatever your modem is symlinked with or its exact device name.)
Lastly,
just type in wvdial 
Hope that is of any help.

---

### Post by xoros on 2006-06-12
This also works good. 
1. sudo vi /etc/wvdial.conf
2. hit "i" for insert mode 
3. make sure Modem = /dev/"your exact name here" and enter your "phone =" "username =" and "password ="
4. hit "esc" to exit insert mode
5. ":wa" to save, then ":q" to quit
6. Run "sudo wvdialconf /etc/wvdial.conf"
7. If that went good wvdial will have automatically correctly set up your "wvdial.conf"  Check changes with: "vi /etc/wvdial.conf"  (":q!" to exit)
8. "sudo wvdial" and wait till after it shows primary and secondary dns addresses and a couple "pppd:" lines
9. use internet.
10. when done select the wvdial screen and hit "ctrl+c" to disconnect gracefully.
Hope that was verbal enough :)

---

### Post by xoros on 2006-06-12
Would like to know is there any way to get modem lights applet installed? or something similar in kubuntu?

---

### Post by golfbuf on 2006-06-12
>Well here's some more information. I enter the coes to configure wvdial. It scans my ports and then puts out: 
>Sorry, no modem was detected! Is it in use by another program? Did you configure it properly with setserial?

Normally an external serial modem will be detected by the kernel and assigned to port ttyS0 or ttyS1 .. On my dapper, doing 'dmesg | grep -i tty' shows:

[4294670.452000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

this tells me that it is properly setup in the kernel configuration and will be assigned ttyS0.  So, I can't see why your wvdial.conf from breezy won't work.  Maybe you ought to post it, so we can comment further.


>I tried pppconfig to set up my Earthlink account. It's so confusing. Especiall the static/dynamic wierd stuff.

The static or dynamic question refers to the type of domain you are assigned.  Generally, dialup users get a different domain number assigned at each connection, so you should select dynamic.

BTW, kubuntu has a nice dialer, called kppp that works fine here.  Also, I've tried the gnome modem monitor and it works also.

regards,

---

### Post by golfbuf on 2006-06-12
[QUOTE=xoros]Would like to know is there any way to get modem lights applet installed? or something similar in kubuntu?[/QUOTE]

kubuntu has kppp.  Also, if you search kde-apps.org, you will find kmodemlights.  It's just like the old gnome modemlights except it works on KDE!

For gnome, try using the 'System Monitor' on the panel, then right click and select 'preferences' .. on the preferences, check the 'Network' box.  This will give you a box that shows ppp0 activity, kind of like the old modemlights.

regards,

---

### Post by golfbuf on 2006-06-12
[QUOTE=Patb]but one problem I have not been able to overcome is that Dapper will always dial my ISP at startup.  What program is actually initiating this connection at startup, I have no idea.  Any suggestions on how to find out would be welcome.[/QUOTE]

Yes, I had the same problem with my dialup starting during the boot process.  I had posted a message on the mailing list, but not here.  It seems there's a bug in gnome network setup that adds 'auto ppp0' to /etc/network/interfaces .. and /etc/network/interfaces gets activated when the boot "starts the network".  Anyway, the fix is to open it in an editor and remove the 'auto ppp0' from that file.

regards,

---

### Post by zxee on 2006-06-12
In my experiance gnome-ppp is DOA in dapper. Modem monitor works provided you edit /etc/chatscripts, and while it works it is inconsistent  e.g sometimes, like if the connection drops, it won't dial out again and requires a re-start to work. Also the settings in modem monitor don't get saved, but that's the reason for editing /chatscripts. I do have my connection working but I wouldn't give the set up or functioning praise. Since breezy worked so well I'm somewhat annoyed.

---

### Post by xoros on 2006-06-13
[QUOTE=golfbuf]kubuntu has kppp. [/QUOTE]

I can't get kppp to work.  WVdial works fine though. 

When I try kppp it says connected and then logging in and just hangs there.... it never logs in and eventually times out and restarts.  Not sure what is wrong?? 

Thanks for the info on the apps. Here is the link to kmodemlights home page: [http://www.forwiss.uni-passau.de/~berberic/Linux/kmodemlights.html](http://www.forwiss.uni-passau.de/~berberic/Linux/kmodemlights.html)

---

### Post by golfbuf on 2006-06-13
[QUOTE=xoros]I can't get kppp to work.  WVdial works fine though. 

When I try kppp it says connected and then logging in and just hangs there.... it never logs in and eventually times out and restarts.  Not sure what is wrong?? 
[/QUOTE]

Yes, it's explained in the kppp help troubleshooting section .. you have to edit /etc/ppp/options and comment out the line that says "auth".  Then kppp connects ok.

regards,

---

### Post by xoros on 2006-06-13
[QUOTE=golfbuf]Yes, it's explained in the kppp help troubleshooting section .. you have to edit /etc/ppp/options and comment out the line that says "auth".  Then kppp connects ok.[/QUOTE]

Actually I just un-commented "#noauth" in etc/ppp/peers/kppp-options 

and then set my authentication method to "script based" and set up a login script.

Worked! 

Thanks for your help though :)

---

### Post by bigfinch4991 on 2006-06-15
Wow! I went away for vacation for a week and I come back to find all of these wonderful solutions! Thanks everyone! I'm going to see what I can figure out. If I get anywhere I'll post my results. And for anyone else using this thread as their only hope for Dapper Dialup, hang in there! I'm in this mess too. Thanks again.

---

### Post by Patb on 2006-06-16
Re dialup always starting during the boot process:  Thanks for the hint Golfbuf - spot on!  

I have played around further with /etc/network/interfaces and rather than removing the ppp interface there I edited it to suit my system.  I have already configured a ppp provider called "ozemail" using pppconfig so I changed the lines 
```
iface ppp0 inet ppp
provider ppp0
```to
```
iface ozemail inet ppp
provider ozemail
```
I then made sure my provider options file /etc/ppp/peers/ozemail included the demand option which enables an interface to be configured and established but not connected until data traffic is present (ie until my browser or other program tries to connect to the internet).  

This is probably fairly crude but it suits my needs: a stand alone desktop with dialup.  I hope it's of use.  

Cheers, Pat

---

### Post by chuckman78 on 2006-06-22
I didn`t catch this thread untill today. I used to have Breazy installed in my box and I used (and keep using) a US Robotics external modem (conected to COM1) as my internet connection. I juste needed to use gnome-ppp and voila! the connection worked flawlessly. Dapper has been another story thought. I have tried gnome-ppp, wvdial (which is the base for gnome-ppp), pppconfig, modem appplet but no joy after all. The connection begins, the modem chirps, but right in the middle of the thing it drops the connection during transaction with the ISP side. I always get a "Carrier not detected)" (even when I specified no carrier detect in gnome-ppp) or "dialup time out". Then I go back to my XP partition and the modem works great as always.

This problem is getting very irritating and frustating. I really would like to use Ubuntu but looks like Ubuntu doesn`t like me!


Regards,

Carlos.

---

### Post by golfbuf on 2006-06-22
[QUOTE=chuckman78]The connection begins, the modem chirps, but right in the middle of the thing it drops the connection during transaction with the ISP side. I always get a "Carrier not detected)" (even when I specified no carrier detect in gnome-ppp) or "dialup time out".[/QUOTE]

Maybe we could help more if you posted your /etc/wvdial.conf (edited to remove your actual phone no., username, and password, of course), the results of running "sudo wvdialconf /etc/wvdial.conf" in a terminal, and the results of running "sudo wvdial" in a terminal.  You should be able to copy these over to XP and post them.

Sometimes it helps to add "Stupid Mode = yes" in /etc/wvdial.conf.  Also, another option you can try is "Carrier Check = no".  Try these separately and together and let us know.  You can also get great assistance from very experienced helpers at the linmodems.org mailing list.  You definitely want to stop there before giving up on linux!

regards,

---

### Post by golfbuf on 2006-06-22
[QUOTE=Patb]included the demand option which enables an interface to be configured and established but not connected until data traffic is present (ie until my browser or other program tries to connect to the internet).[/QUOTE]

I tried demand dialing once upon a time and found that by the time my modem dialed and connected that the web browser or email client (or whatever was trying to connect) would give up.  What's your experience regarding this?

regards,

---

### Post by one norse on 2006-06-22
[QUOTE=golfbuf]I tried demand dialing once upon a time and found that by the time my modem dialed and connected that the web browser or email client (or whatever was trying to connect) would give up.  What's your experience regarding this?

I have the same problem in Kubuntu 6.06. I had kppp working great in 5.10, but now that I've upgraded, I cannot seem to get connected. ](*,)  I found the noauth problem mentioned in other threads/forums, and now kppp will dial and connect. Now with the connection seemingly made, Adept and Konquerer don't seem to be able to use it. 

I recall having to set up something in networking to make this bridge, but I cannot seem to find the correct system settings in Dapper to set up a ppp connection. :-k

---

### Post by zxee on 2006-06-22
> I recall having to set up something in networking to make this bridge, but I cannot seem to find the correct system settings in Dapper to set up a ppp connection. 

What's in /etc/resolv.conf? Is it a blank file-it shouldn't be.

---

### Post by chuckman78 on 2006-06-22
Hi golfbug, and thanks for your time and help.

I tried the “Stupid mode = yes” suggestion and the other option too but no luck at all.

Below is the sudo wvdialconf /etc/wvdial.conf log:


carlos@mbubuntu:/etc$ sudo wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 5601
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Port Scan<*1>: S10  S11  S12  S13  S14
ttyS15<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS15<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS15<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S16  S17  S18
Port Scan<*1>: S19  S20  S21  S22  S23  S24  S25  S26
Port Scan<*1>: S27  S28  S29  S30  S31  S32  S33  S34
Port Scan<*1>: S35  S36  S37  S38  S39  S40  S41  S42
Port Scan<*1>: S43  S44  S45  S46  S47  S48  S49
ttyS50<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS50<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS50<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS51<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS51<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS51<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS52<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS52<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS52<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS53<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS53<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS53<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

This is my wvdial.conf file:

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
Carrier Check = no
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = ,X,XXXXXXXXXXX
Username = XXXXXXXXXXXX
Password = XXXXXXXXXXX

And here the result of sudo wvdial:

carlos@mbubuntu:/etc$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT,X,XXXXXXXXXXX
--> Waiting for carrier.
ATDT,X,XXXXXXXXXXX
NO CARRIER

(HERE, THE MODEM BEEPS AND CHIRPS AS NORMAL BUT ABRUPTLY STOPS AT SOME POINT)

--> No Carrier!  Trying again.
--> Sending: ATDT,X,XXXXXXXXXXX
--> Waiting for carrier.
ATDT,X,XXXXXXXXXXX
--> Timed out while dialing.  Trying again.
--> Sending: ATDT,X,XXXXXXXXXXX
--> Waiting for carrier.
ATDT,X,XXXXXXXXXXX
Caught signal #2!  Attempting to exit gracefully...
--> Disconnecting at Fri Jun 23 22:40:02 2006

It looks like if at some point the ISP hangs me out. I think I have read something about a “noauth” problem, does it got something to do with this? Once again, thanks for your time and help.

Regards,

Carlos.

---

### Post by zxee on 2006-06-23
Well I haven't been much help with this problem-but I'll keep trying. The auth/noauth choice is in your /etc/ppp/options and in the /etc/ppp/peers/your-isp-name file you can use this command  >  egrep -v '#|^ *$' /etc/ppp/options to find what is selected.  

I think this > --> Waiting for carrier.
ATDT,X,XXXXXXXXXXX
NO CARRIER  is the problem. 

I don't know why the modem isn't seeing a carrier though. Check out your /etc/ppp/peers /yourispname file it should contain the noauth line in it. see mine here:

# This optionfile was generated by pppconfig 2.3.10. 
# 
#
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/*****blanked"
debug
/dev/ttyS0
115200
defaultroute
noipdefault 
user ******blanked
remotename *********blanked
ipparam *******blanked

usepeerdns

---

### Post by one norse on 2006-06-23
[QUOTE=zxee]What's in /etc/resolv.conf? Is it a blank file-it shouldn't be.[/QUOTE]

It has one line: 
nameserver 192.168.0.1

I probably should also mention that Breezy did not recognize my built-in network chip, but Dapper found it right away.

---

### Post by golfbuf on 2006-06-23
[QUOTE=chuckman78]Caught signal #2!  Attempting to exit gracefully...
--> Disconnecting at Fri Jun 23 22:40:02 2006

It looks like if at some point the ISP hangs me out. I think I have read something about a &#8220;noauth&#8221; problem, does it got something to do with this?[/QUOTE]

hmmm .. signal #2 .. "man pppd" has error codes near the end, and it says:

      2      An error was detected in processing the options given, such as two mutually exclusive options being used.

maybe you have both "auth" and "noauth" selected in your /etc/ppp/options.  When I do "egrep -v '#|^ *$' /etc/ppp/options", I get:

asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 17
lcp-echo-failure 3
noipx

See how this compares to yours.  It may be a function of your ISP .. whether to use "auth" or "noauth" or neither.  Consider editing your /etc/ppp/options to try these alternatives.

regards,

---

### Post by golfbuf on 2006-06-23
[QUOTE=one norse]It has one line: 
nameserver 192.168.0.1

I probably should also mention that Breezy did not recognize my built-in network chip, but Dapper found it right away.[/QUOTE]

It just worked here, but I have no network card.  So, do you think the network configuration set you to connect via the network card instead of ppp0?

In a terminal, use "ifconfig" and "route" to see what's configured when you've made your dialup connection.  For me, ifconfig just shows "lo" and "ppp0" and "route" shows the default line is connected by ppp0.

golfbuf :~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13461 (13.1 KiB)  TX bytes:13461 (13.1 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:<snipped>  P-t-P:<snipped>  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7517 errors:2 dropped:0 overruns:0 frame:0
          TX packets:6986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:5284024 (5.0 MiB)  TX bytes:1758229 (1.6 MiB)

golfbuf :~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<snipped>          *               255.255.255.255 UH    0      0        0 ppp0
default              *                     0.0.0.0         U     0      0        0 ppp0

  If you have some other network showing, then you need to configure your network again .. perhaps via "System Settings => Network Settings" to use ppp0 instead of the network card.  I haven't done that because I didn't have a network card.  If it's not obvious how to do it, check the wiki or howto's.

regards,

---

### Post by one norse on 2006-06-23
[QUOTE=golfbuf]

  If you have some other network showing, then you need to configure your network again .. perhaps via "System Settings => Network Settings" to use ppp0 instead of the network card.  I haven't done that because I didn't have a network card.  If it's not obvious how to do it, check the wiki or howto's.

regards,[/QUOTE]

I did ifconfig, and got entries for eth0 and lo, but nothing like ppp0 listed. 
After reading the help pages for System Settings=>Network Settings, it appears that the network must be present on the system as it is set up, and since the modem isn't set up during installation, it doesn't show up as a network device. It must be assuming that if I have a network card, that is how I must want to connect to the internet. 'Network Settings' does not list ppp0 at all, either. I tried pppconfig, but that did not seem to help. Are there any other configuration scripts I should know about?

thanks

---

### Post by gray-squirrel on 2006-06-24
[QUOTE=xoros]Actually I just un-commented "#noauth" in etc/ppp/peers/kppp-options 

and then set my authentication method to "script based" and set up a login script.

Worked! 

Thanks for your help though :)[/QUOTE]

What should be in the login script?  I'm going to try this next; playing around with the auth/noauth line had no effect for me.  I'm going to give kppp another chance this weekend.

In the meantime, kmodemlights has been up since early Friday morning and running very nicely.  And since this morning, I can even disconnect from it.  It's as if the "good old days" are back as far as my computer is concerned.  Thanks for posting the link to the program.

---

### Post by TheTank on 2006-06-24
Running Dapper on an old pc (mother-in-law) with a US Robotics and the internet connection runs fine as long as I do not close the System->Admin->Network Window.
Also the volume does nothing.

If I am starting to really like Ubuntu. Though the update from badge killed it I was able to get it running in a few hours via a fresh install.
I intend to install ubuntu server on my private server at home.
If I can get the above mention problem removed I will really think about installing it on my main sys.

---

### Post by one norse on 2006-06-25
For what it's worth, my dialup is finally working in Dapper Drake! The problem I had seems to be that the network configuration routine in the installer assumed that my machine's built-in network card was the way in which I wanted to connect to the internet, and did not leave me the dialup option. 
Here are the steps that got dialup working for me:

1) Re-boot, shut off the built-in ethernet adapter on my mother board in bios.
2) Re-install Kubuntu 6.06 (I'm not sure I needed it, but I thought a fresh start would be good.) 
3) Ran pppconfig. (again, not sure if necessary, but it didn't hurt.)
4) Set up connection, modem in kppp. (including putting noauth in the options screen).
5) changed auth to noauth in /etc/ppp/options
6) uncommented the noauth line in /etc/ppp/peers/kppp-options (again, maybe unneccessary)
7) Hit connect, it dialed, connected, and worked! (It appears that  kppp sets up the ppp0 connection if it doesn't find another network. )

8) Reboot, enable onboard ethernet, try to dial out. FAILURE! Get connection in kppp, but no communication with browser. 
9) After reading back through this thread, I found Patb's post on June 16 about changing /etc/network/interfaces. There was no line in my /etc/network/interfaces file about ppp0 at all (I assume it was re-written when my onboard ethernet was added) so I added:

iface ppp0 inet ppp
provider ppp0

as in Patb's post, 
10) Reboot, and now it works again (in fact, I'm posting from that machine now) :-D 

Now, my ethernet port is not configured properly, as it was before all of this, but it is recognized, and is my next project.

Thanks to those who offered suggestions,
I hope this helps if someone else finds the same problems.

---

### Post by Patb on 2006-06-26
[QUOTE=golfbuf]I tried demand dialing once upon a time and found that by the time my modem dialed and connected that the web browser or email client (or whatever was trying to connect) would give up.  What's your experience regarding this?[/QUOTE]
Yes, that often does happen.  But I haven't found it a big hassle.  I just hit 'Reload' or whatever.  

Cheers, Pat.

---

### Post by editrix on 2006-06-27
I'd just like to keep this thread alive because there are a lot of people (including me) still on dialup, especially in rural areas--even in North America.It looks like we're going to have a lot of problems switching to Dapper.

---

### Post by chuckman78 on 2006-06-28
Guys, right now I have almost given up with my external USRobotics modem. Right now I am trying a winmodem with an Intel 537EP chipset. Details at the thread:

[http://www.ubuntuforums.org/showthread.php?t=205432](http://www.ubuntuforums.org/showthread.php?t=205432)

Thanks all for your kind help and time. I will try again later.

Regards, 

Carlos.

---

### Post by bigfinch4991 on 2006-07-02
Hey all, been very busy with work lately :mad: . I tried some things suggested. Here's my outputs (in .gif format). If anyone could make sense of these things and tell me solutions, I would be forever grateful.

---

### Post by golfbuf on 2006-07-03
[QUOTE=bigfinch4991]Hey all, been very busy with work lately :mad: . I tried some things suggested. Here's my outputs (in .gif format). If anyone could make sense of these things and tell me solutions, I would be forever grateful.[/QUOTE]

Yes, well you said earlier that you have an external serial modem, so the sl-modem software driver won't help.  It seems like your modem is not working.

I can think of a few other things to try to troubleshoot:

1.)  try connecting the modem and having the power switched on before booting up.  After boot up, open a terminal, and enter 'dmesg | grep -i tty' and see what messages appear.  If any errors appear, enter the exact error message in a google search.

2.) I'm curious what might appear in your logs when you have it connected and turn the power on and off.  You can open 3 terminals and execute 'tail -f /var/log/syslog' in one, 'tail -f /var/log/messages' in another, and 'tail -f /var/log/kernlog' in the 3rd.  Then you will see the messages reflect what the kernel sees by the power going on and off.  If nothing appears, then maybe you've got to go back to windows again to be sure the modem works.  If some error message appears, then try entering it into a google search.

3.) The only other thing I could suggest is trying the scanModem tool from linmodems.org.  That tool uses a different approach to identify the modem.  Also, their mailing list is a good resource for ideas.

HTH,

---

### Post by Patb on 2006-07-05
[QUOTE=bigfinch4991]Hey all, been very busy with work lately :mad: . I tried some things suggested. Here's my outputs (in .gif format). [/QUOTE]
Bigfinch,  Dapper seems to have trouble detecting a dialup modem.  I had to tell it where to look for mine.  The device name is case sensitive and I think yours will be /dev/ttyS1 not /dev/ttys1 which you have written.  I would like more information anyway.  Could you post the output of: 
```
dmesg | grep -i tty
```
I would suggest you go back to pppconfig and set up a connection there.  Choose 'dynamic' not 'static' and where it tries to autodetect your modem, skip that and enter the device name, presumably "/dev/ttyS1", manually.  

Now if the connection you have set up with pppconfig is called say "fred", could you post the output of:
```
pppd call fred dryrun
```
Delete any personal bits of course.  

Cheers, Pat

---

### Post by one norse on 2006-07-05
[QUOTE=editrix]I'd just like to keep this thread alive because there are a lot of people (including me) still on dialup, especially in rural areas--even in North America.It looks like we're going to have a lot of problems switching to Dapper.[/QUOTE]

Ditto here. 

An update: I've gotten kppp working, but there is a conflict with eth0, so that I must disable eth0 in order for my email and browser (and adept) to communicate over dialup. Another thread started on this problem, so if I figure out a solution, I'll post there.

---

### Post by bigfinch4991 on 2006-07-10
FIXED. WORKING! PROUDLY TYPING FROM AN UBUNTU LINUX BOX WITH DAPPER DRAKE and ALL CURRENT UPDATES! Haha, THANKS to everyone for their help. I'm typing from firefox right now while I'm installing some new software to my Gnome desktop. I'm so happy to have this internet working. Here's the unfortunate bad news: I have no idea what I did. So I'm happy but frustrated for all those who haven't had their interenet problems fixed. I'll try to go through a few things I did that might've made my internet work.
1. Try running some tests and copy and pasting your outputs for the smarties in this forum to see and help you. (Basically anything in the Terminal window.) 
2. Just get a serial modem. Mine cost 9 dollars from Amazon.com (hmm, maybe that's why it didn't work, ah well). They're very cheap and more reliable than those doggone Winmodems.
3. ttyS0 and ttyS1 are the most common ports that serial modems plug into. Mine happened to be at ttyS0 all along.
4. WVdialer is the best way to get to the internet in my opinion. Gnome PPP works very well too.
4. No idea if this did anything: While the computer was booting up, I turned off, then turned back on the modem. It worked after that and me running a few tests that were suggested in this thread.
5. NEVER GIVE UP! Ask dumb questions (because they're usually not), if you're a newbie, say so and try other forums too.
6. Something in one of these posts in this thread helped me, maybe it will also help you. Follow the threads from start to finish and don't jump into the middle of them. Trust me, I've tried and just ended up being confused. 

Good luck to all with problems. Trust me, this won't be the last time you see me posting in these parts. Have an excellent day,
                   Al Arandal

---

### Post by golfbuf on 2006-07-14
> **bigfinch4991 said:**
> 
2. Just get a serial modem. Mine cost 9 dollars from Amazon.com (hmm, maybe that's why it didn't work, ah well). They're very cheap and more reliable than those doggone Winmodems.

I can't believe you actually got it for $9 .. did that include shipping?  Yes, I have seen some auctions on eBay with bids of less than $10, but they always added shipping of $15 or more.  Was your Amazon a one time deal or is it still available?  Link would be appreciated.

regards,

---

### Post by one norse on 2006-07-16
> **one norse said:**
> 
An update: I've gotten kppp working, but there is a conflict with eth0, so that I must disable eth0 in order for my email and browser (and adept) to communicate over dialup. Another thread started on this problem, so if I figure out a solution, I'll post there.

Further update:Adding'defaultroute' and 'replacedefaultroute'  at the end of the /etc/ppp/options file forced my machine to use ppp0 as the default network, and enabled it to connect with the internet.

---

### Post by baroing on 2007-03-18
Looks like I'm months late finding this thread, but, chalk one more dial up ubuntu user out there.....

I had similar problems with getting online via dialup..luckily before I started, a co-worker kindly lent me his external serial modem, and another helped me get that modem set up....

I'm a complete Linux newbie, Kubuntu Dapper Drake is my first distro...but I digress..

KPPP would just not work for me.  My ISP guy runs Slackware, but byeond that he didn't really 'do' much for me...

I did a quick search online at work and found a forum post for KPPP 'how to'...

wvdial wasn't giving me any love, but the second method (sudo pppconfig) worked like a charm and I'm still using <pon> to connect to this day.

---

### Post by sharong on 2007-04-18
Don't give up - I got my connection to work fine with a built-in PCI Winmodem on a laptop.  Once I got the modem set up, I registered with uklinux as my ISp and they gave really helpful instructions.  Once I'd done all that, I got connected on the first go!

---

### Post by Bartender on 2007-04-19
sharong -
Could you share any details?  An easy to configure winmodem would be a wonderful thing.  

Read thru this thread with interest.  
My Dapper dial-up experience (and I didn't know what I was doing):

Bought a couple of old USR Sportster externals (model 0701) on ebay.  The #3, 5, and 8 switch settings on the back of the modem were all down.  The rest were up.  I didn't know what to do with them so left 'em alone.  Figured out how to get the modems working on the Windows side of my PIII dualboot W2K/Dapper PC and flashed them to latest firmware at 3com website.  They both worked in Windows but felt slower than the $12 Intel 536 winmodem. 

So, back to Ubuntu.  With the modem plugged in and turned on, booted Dapper, went into Networking.  It auto-detected the USR on tty0.  Typed in the username, phone #, password.  Closed Networking.  Found the Modem Monitor applet in "Add to Panel".  
Dialed.  It worked.  Connection was noticeably slower than Windows.  Then Juno cut me off after a few minutes.  Juno is non-functional with Linux.  The old Juno 5 is anyway.  My guess is their servers look for a fingerprint from the connecting PC and if they don't see it you're cut off.  If we weren't getting it for so cheap I'd switch to ISP.com or Copper.net or some other ISP that requires no proprietary software.

I haven't tried wvdial or ppp.

To the folks who've had troubles with Dapper and their externals - I wonder if this was something having to do with their hardware?  Because on my old PIII/ASUS motherboard Dapper seemed to communicate just fine with the modem.

EDIT:  Has anyone tried either of these?  The very cheapest one at Newegg looked sketchy, but comments on the next two both indicated Linux successes
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825137104](http://www.newegg.com/Product/Product.aspx?Item=N82E16825137104)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)

---

