---
title: "Dial-up networking in Lucid Lynx 10.01"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by ed bear on 2011-02-16
I've been running 8.04 Hardy since its first release, and was hoping to deal with its loss of support by going to 8.10 but learned that it has already been dropped.

So I'm back to installing 10.04 - and up against the bizarre choice to drop dial-up networking!  Fortunately, I have my 8.04 machine still live, and I've researched it extensively without success.

The best summary of what I've done follows this post I found online:

-----QUOTE-----
forums.techguy.org/linux-unix/927230-solved-trouble-setting-up-dialup.html
number9's Avatar 	
number9 number9 is offline
Junior Member with 25 posts.
	  	
Join Date: May 2010
Experience: Beginner
05-Jun-2010, 12:04 AM #1
Solved: Trouble setting up dialup in Ubuntu 10.04
I'm having trouble setting up dialup in Ubuntu 10.04.

As an Ubuntu noob, I read many threads about dialup, including those on this forum; made sure to get an external hw modem [USRobotics 5637 USB, advertised as controller-based and tested to work in Linux], to avoid the softmodem/winmodem problem.

Using the 10.04 LiveCD, I installed the four .deb packages that are in \pool\main\w\wvdial\ and in \pool\main\w\wvstreams\.

Now I'm stuck because I get errors when I try command line stuff, errors like "cannot open /dev/modem" and "can't find /dev/modem in /etc/fstab or /etc/mtab"

I'm confused; I've read so many threads with so much different info that I can't sort it out. Maybe I'm following info that applied to earlier versions of Ubuntu. Every error I try to fix leads to more errors. Can someone suggest a constrained, step-by-step procedure to ensure I've mounted the modem, added myself to whatever groups, and whatever else I need to do?

I know there's no wizard to make it simple, but is there a checklist or something to help me sort this out? I have the ISP info, DNS primary+secondary server numbers, phone numbers, etc. Is there a UI/graphical path, instead of command line? Had no idea this would be so difficult.

Thanks for help--
Register for free to hide this ad!
lotuseclat79's Avatar 	
lotuseclat79 lotuseclat79 is offline
Distinguished Member with 19,582 posts.
	  	
Join Date: Sep 2003
Location: -71.45091, 42.27841
05-Jun-2010, 12:10 PM #2
Hi number9,

First things first, in Linux, it is not default to associate /dev/modem with a serial port, however, the easiest thing to do is to issue the following command from a Terminal window for command-line commands:
$ sudo ln -s /dev/ttyS0 /dev/modem
then check it with the command:
$ ls -lt /dev/modem
and you should see something like:
lrwxrwxrwx 1 root root 10 2007-12-12 12:27 /dev/modem -> /dev/ttyS0

And then, try following Setting up Dial-up connection in Ubuntu.

Also, read post #4 of the thread: Dial up internet with Linux which explains how to setup and use wvdial.

-- Tom
------END------

Ed Bear again here - I had no trouble creating the serial port link, but installing the packages was another matter.

I copied the four files (.deb packages for vwdial, libuniconf4.6... , libwvstreams4.6...-base, libwvstreams4.6...-extras) as well as gnome-ppp to my /var/cache/apt/archives directory, which is where I have previously placed things downloaded on the high-speed terminals at my local library and brought home to install on 8.04 successfully.

I opened a terminal, became root, and ran ug+rwx, successfully marking them all rwx and making sure that both my user and root groups included my user and root accounts.  Also the modem group.

Then I ran

apt-get install gnome-ppp

or any of the others, or even 

apt-get install g*

or other configurations, I got

Can't find package (whatever)

Term showed the files in green after setting the proper (I think) permissions.  Even using cut-and-paste to avoid misspellings failed.  And I tried with and without the .deb suffix.

Remember, the new machine has NO net access.  Synaptic and Update Manager could not show the files, nor could they run their checks because I have no net access on that machine.

What am I doing wrong that's stopping apt-get from "finding" the files in the directory I'm installed to?

And, of course, does anyone know a better way to set up dial-up networking for Lucid Lynx 10.04?  

Is there a good document on the process out there anywhere I haven't found?

Thanks, all, for your help if you can.

ED BEAR
Vancouver, Canada
Running 8.04, trying to get to 10.04!

---

### Post by alexfish on 2011-02-16
Hi

Not sure if this will help but worth reading .

Ubuntu **10.04** includes **wvdial** and dependencies but are NOT installed!
To install them read [wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")

---

### Post by ed bear on 2011-02-16
Sorry, folks - I checked my message carefully before posting, but then I screwed up the thread title (10.01 instead of 10.04) and misspelled one keyword as "netwroking" after pasting in the message!

Hope it can be fixed for reference...

Thanks for the pointer, Alexfish!  I will get to it...

Meanwhile I wanted to report that I made some progress!

When I tried to install the packages from Gnome by navigating to /var/cache/apt/archives and then just selecting the gnome-ppp or all the packages and launching them, I got one or a set of windows complaining about unsatisfied dependencies.   BUT...

After posting here and going back to work on it, I tried each of the packages separately, and realized that one did not have a dependency failure.  By trial and error after each one, I realized that the packages have to be installed in a particular order:

libwvstreams4.6...-base
libwvstreams4.6...-extras
libuniconf...
wvdial..
gnome-ppp

(version details in the packages will vary as time goes on, so I left the ellipses in them)

The post Alexfish pointed to did detail things, but failed to mention the required sequence, so I hope I've added some useful info to the database!

Now I'll go back and struggle with the modem for a while, but thanks to more thinking and Alexfish's help, I think I'm on the right track!
ED BEAR

---

### Post by ed bear on 2011-02-21
Hi again, folks.  More progress, but no victory yet...

I am now able to initiate dial-up, connect to my ISP and negotiate a login successfully.  Since the connection persists, I know that my userid and password have worked, but neither Firefox nor Synaptic or Update manager think they have a connection.  I've searched all manner of settings and on-line resources - anyone seen anything that might help?

ED BEAR

---

### Post by alexfish on 2011-02-22
Hi

if using wvdial
can post the results of wvdial from the terminal

or give details of which method been used for the connection

alexfish

---

### Post by stevenh512 on 2011-02-22
> **ed bear said:**
> Hi again, folks.  More progress, but no victory yet...

I am now able to initiate dial-up, connect to my ISP and negotiate a login successfully.  Since the connection persists, I know that my userid and password have worked, but neither Firefox nor Synaptic or Update manager think they have a connection.  I've searched all manner of settings and on-line resources - anyone seen anything that might help?

ED BEAR

I'm stuck with dial up internet where I live, and I've run into this same problem with 9.10 and 10.04. The easiest workaround I've found is to right-click the Network Manager icon in your notification area (right side of the top panel for a standard GNOME Ubuntu install) and disable networking before you dial up with GNOME-PPP. It's a little inconvenient for me since I can't access a network share on the Windows machine in the other room while I'm online, but it works lol

---

### Post by ed bear on 2011-03-04
TO SUBMIT
Hello again, folks - this has been a rather trying quest, from not being able to copy the log file in gnome-ppp to having my 8.04 machine's boot setup disabled by "apt-get autoremove" telling me something went wrong and I should run GRUB (which I won't get inot here unless someone can point me to a legendary post about "staring at a brown screen", or a good doc on how 8.04 boots, or how apt-get autoremove can scramble a boot sequence).

OKAY - FIRST - Does 10.04.2 improve this situation at all?  I've been reinstalling things all week, and I'm willing to try that, too, if the issue's been addressed.

Reference: I'm an old and inquisitive geek, experimenting with Linux since the nineties but not running it as a regular system until Feisty Faun, and Hardy Heron has run my main on-line system since July 2009.  It's been so trouble-free that I haven't had to do that much more head-banging experimentation until now.

There's been a lot of moving the modem between machines and re-installing and live-booting my 8.04 machine, and a lot of reading of posts here on the forums.

The connection log showed the modem initalizing and dialing, but lost focus and wouldn't let me scroll or copy the Connection Log window's contents ... until I took a bathroom break by chance, and the window had reclaimed focus again after the modem **** down!

Note that I found hidden files named ".wvdial.conf" in /root AND /home/ed-bear which seemed identical and looked like this:

[.wvdial.conf] in /home/ed-bear:
[Dialer Defaults]
Modem = /dev/ttyS0
ISDN = off
Modem Type = Analog Modem
Baud = 115200
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = 
Init4 = 
Init5 = 
Init6 = 
Init7 = 
Init8 = 
Init9 = 
Phone = 604-681-1527
Phone1 = 
Phone2 = 
Phone3 = 
Phone4 = 
Dial Prefix = *67,,
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = [*** DELETED FOR POSTING (wow - it's in plain text!) ***]
Username = [*** DELETED FOR POSTING ***]
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off [*** what's this? it's = off in my working 8.04 ***]
Idle Seconds = 0
Auto DNS = on
;Minimize = off
;Dock = on
;Do NOT edit this file by hand!
[END .wvdial.conf]

In /etc, there were two more copies, one named .wvdial.conf and another wvdial.conf - I think one of them was originally the default, unconfigured form but it was overwritten.  Trying to edit these files to put a marker character into the "malformed" last line never got the marker to appear, but the file in /home/ed-bear kept reverting to the original final line which never ended with a linefeed or carriage return, BTW.  I suspect it was the line that was used, and that gone-ppp or wvdial overwrote the line on exiting.  By checking Modified dates, I conclude the /home/ed-bear version of .wvdial.conf is being used for dial-out.

The version in /home/ed-bear/.wvdial.conf - which is what I'm using on 8.04 ro call you right now - is 100% identical, down to the malformed last line with no CR or LF - save that it hasn't stored my dialing prefix, which suppresses caller ID and should have zero effect once a call is made.

BUT - I'm connecting here via the network admin applet.  During one of my installs of 8.04 this week, I was able to get gnome-ppp working perfectly on 8.04, and it was more convenient, but the next reinstall worked only with the network admin applet, which does not support dial-up on 10.04!  I don't know if the applet uses gnome-ppp's configuration file or something else I haven't found.

[ORIGINAL /etc/wvdial.conf]
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes
[END ORIGINAL .etc.wvdial/wvdial.conf]

NOTE: personal and ISP info have been concealed below.

[CONNECTION LOG CONTENTS]
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*67,,,604-681-1527
--> Waiting for carrier.
ATM1L3DT*67,,,604-681-1527
CONNECT 44000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.            <*** ALL OK TO HERE
--> Connected, but carrier signal lost!  Retrying...  <*** MODEM LIGHTS
                                                           STAY ON!  WHY?
--> Sending: ATM1L3DT*67,,,604-XXX-XXXX               <*** NO REDIAL OCCURS!!!
--> Waiting for carrier.                              <*** ISP RESPONDS...
                          _
                         (_)
   This system is property of XXXX Communications
Disconnect IMMEDIATELY if you are not an authorized user
     Contact xxxx@xxxx.ca for more information
User Access Verification
Username: 
Username: 
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT*67,,,604-XXX-XXXX
--> Waiting for carrier.
Username: 
Username: 
% Username:  timeout expired!
Username: 
% Username:  timeout expired!
Username: 
% Username:  timeout expired!
NO CARRIER
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!             <*** MAXTRIES SET TO 1
--> Disconnecting at Thu Mar  3 08:35:41 2011
[END WINDOW LOG]

Now, this looks a lot like the username is never being sent, and thus the password is never requested.  Note that the program seems to be detecting and communicating with the modem just fine.  Any ideas, folks?
ED BEAR
Vancouver, Canada
8.04 Hardy on AMD 850 MHz/
10.04 Lucid on Intel 2.2GHz (in progress)

---

### Post by alexfish on 2011-03-04
Hi

looks as if your diagnostics may be correct

try adding in your wvdial.conf connection details

```
stupid mode = 1
```[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm](http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm)

ADDED:

sometime a good idea to limit the dial attempts, this will hopefully prevent wvdial looping forever in the dial mode, 3 is reasonable

add
```
Dial Attempts = 3
```alexfish

---

### Post by ed bear on 2011-03-04
Thanks for the rapid response, Alexfish, but it looks like we just made the system dieties angry, even a bit impolite.  I removed the dialing prefix and set "stupid mode = on," and while dialing and synch worked...

[CONNECTION LOG]
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.           <*** WTF?
--> Initializing modem.                               <*** Perhaps ok...
--> Sending: ATZ
ATZ
OK                                                    <*** Modem's there...
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT604-681-1527
--> Waiting for carrier.
ATM1L3DT604-681-1527
CONNECT 45333/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Mar  4 12:32:05 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 1410
[END CONNECTION LOG]

Well, now, look at this... /etc/ppp/pap-secrets ?  Anyone ever heard of that?  I've made someone's program upset by trying to diddle the text file - how un-LINUX!  But if there's a PAP file in there, it likely has some scripts for login... got to look into it, but that means reconfiguring for the other computer.  I do at least have a USB KVM switch, but with no USB keyboards I have to move them around... and transfer the modem - will sleep first.

Note that I run Dial Attempts = 1.
ED BEAR
Vancouver, Canada
8.04 Hardy on AMD 850 MHz/
10.04 Lucid on Intel 2.2GHz (in progress)
Successful tin-can telephonist.

---

### Post by alexfish on 2011-03-05
Hi

whilst snoozing ,, there is a site here , worthwhile reading when awake

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

 can also suggest asking your provider as to what is required as to the protocols

for getting connected, since the dial up works, there can only be two stages to complete

the connection as regards ppp, maybe the above site can jog your memory as to what you had to do in Ubuntu 8.04 to get a connection , and hopefully work in 10.04

regards

alexfish

---

### Post by ed bear on 2011-03-12
Alexfish, I read that mobile dial-up HOWTO and it was very informative, but not in the end helpful.

It contained info about some of the things we uncovered, though it didn't spend much time on pap and chap because its focus was mobiles, which are identified by SIM and don't really need authentication at that level.

Let me note that I did, about a month ago, get gnome-ppp to work reliably for weeks on my 8.04 machine... in the install that was eaten by a blown disk controller.  Since then, and this week with several tests on fresh 8.04 images, I have been unable to get it to work.

Sticking to the one machine, then, I kept testing and trying.

pap-secrets and chap-secrets do exist and are properly configured with logon data from my wvdial configuration.

I am already a member of the dip and dialup groups, and allowed to use the modem (hardly surprising since I'm able to control the modem).  Disabling the Network Administration applet, after disconnecting it from tty0, was similarly no help.

Seems to be time to bother the ISP - though of course they will roll their eyes at another Linux guy who doesn't know what to do.  It was pretty smooth sailing when I signed up two years ago, pretty much right out of the box.

Has anyone else trying to get gnome-ppp to work had to dissect the authentication protocols?
ED BEAR
):P

---

### Post by ed bear on 2011-03-13
I've dug up some more history of gnome-ppp debugging - this seems the most relevant:

-----
Old January 23rd, 2008 	  #6
gwbennett
5 Cups of Ubuntu
 
gwbennett's Avatar
 
Join Date: Oct 2006
Location: Wichita, KS
My beans are hidden!
Ubuntu 9.04 Jaunty Jackalope
Send a message via ICQ to gwbennett Send a message via AIM to gwbennett Send a message via MSN to gwbennett Send a message via Yahoo to gwbennett Send a message via Skype™ to gwbennett
	
Re: PPP and modem configuration, help please.
That patch above DOES work for gutsy 32 bit. I use it with m internal sprint evdo modem on my eee. Anyone know how to make the tray icon NOT blink though? I want it in the tray but I don't want it flashing like it's 1997 again.


And WHY has this gnome-ppp update not been packaged and rolled out through udates yet? This tiny bug is due to wvdial's text output haveing been altered. gnome-ppp waits for it to say "connected" and instead now in dumb mode it says "hoping for the best" or some absurdity like that. But how can a bug persist this long unrepaired in ubuntu??
gwbennett is offline
-----
This looks very much like the CHAP problem I'm getting, as its earlier discussion indicates.

This is a Gutsy Gibbon patch, and that's no longer supported.  There's a good bit of evidence that one needs a specific version of gnome-ppp for a given version of Ubuntu.

I wonder what version of gnome-ppp I was using when it all worked?  I'd downloaded it separately from Hardy.  When I tried restoring gone-ppp in Hardy to test it instead of the Network Manager applet, I used the gnome-ppp I found on the Lucid disk.  Then I removed it and installed again using Synaptic, which should have obtained a Hardy-specific one.

I definitely used the Lucid one to get may failures on Lucid.  Attempts to locate older packages via the package pages have so far failed.  Do any of the gnome-ppp users around here know exactly which version they are using?

There are a variety of work-arounds and patches out there.
ED BEAR

---

### Post by Bartender on 2011-03-18
ed bear -

As per my PM, I guarantee you that there's a functional gnome-ppp package in the repos for 10.04.

For any other viewers, a few months back I installed 10.04 to a spare PC.  Hooked a USR external 5686 Sportster model modem to it.  

Typed in ```
sudo pppconfig
``` and set the dialer up.

Got online.  As mentioned in my old dial-up threads, for some reason pppconfig may fail several times with a new connection before it goes thru.  On this PC I tried seven times until it finally connected.

Then you have to go into Synaptic and Reload the packages.  This will take at least an hour on a decent phone line.  Synaptic is worthless until you've Reloaded so it knows where it is and what it needs.  I'm serious about this.  Synaptic will be unable to find packages, and the Hardware Drivers won't work either, until you Reload.

Only then can you create a Package Download Script (PDS).  With a PDS from the dial-up PC, and a laptop, and someone else's fast connection, you can get that dial-up PC updated.

This [thread]("http://ubuntuforums.org/showthread.php?t=1377619") should help if you haven't found it already - the thread has several links that connect to other dial-up threads.  The process for creating a PDS is explained.

So, Reader's Digest if you have a functional ISP and a functional modem -

1) Use pppconfig to get online
2) Reload Synaptic via your horridly slow dial-up connection
3) When it's done, Synaptic will tell you that you need 200+MB of updates.  Ignore that, ask it to get gnome-ppp.
4) Configure gnome-ppp, you should be good to go.

5) If you have access to any broadband at all, create a PDS, get the data, bring it back home, and run it on the dial-up PC.

---

### Post by frank cox on 2011-03-29
Hey Bartender , long time no see. You probably do not remember me but you helped me when I first started in late 09. 
I was playing around in /share/desktop on Isadora {Mint Linux 9] and ran across gnome-ppp and just for the grins I opened it and plugged in a cheap {10.00 I think) USB Winmodem I bought on E-bay that I knew worked on Puppy Linux. Never bothered to try it on Ubuntu as I have a very fast cable connection at the office and use Puppy exclusively on dialup at home. 
Anyway to my shock and amazement considering the first time I tried to set up dial up in Ubuntu was a nightmare that was almost the end of Linux for me I typed my user name  and pword and told it to scan for the modem it found it and connected . These modems are available for 10-15 dollars and they work great ! I am using it now!
It is a bit slow to search ebay so I will edit this post after I  hang up and reconnect on cable with a link to the same modems. I hope this helps you a little after all the time you spent helping me.

Here is the link, when I rebooted it started asking for all the permissions and I ran out of time to settle them all but the modem is still there and dials  , for 11.00 w/ shipping you can't lose!

[http://cgi.ebay.com/USB-56K-Dial-up-Voice-Fax-Data-External-V-90-V-92-Modem-/280453200918?pt=PCC_Modems&hash=item414c503c16](http://cgi.ebay.com/USB-56K-Dial-up-Voice-Fax-Data-External-V-90-V-92-Modem-/280453200918?pt=PCC_Modems&hash=item414c503c16)

This is the Modem Blaster , I bought one for 20.00 w/ shipping, this one is 24.00, still a great deal on a new USRobotics  serial modem even if the plug is a bit odd.

---

### Post by tboy5732 on 2011-03-29
I was having all the same issues. I have worked most of them out and was able to connect using KPPP. My issue now is that I can not find a version of Network Manager that allows me to configure to use the Modem connection. So my modem is connected to the ISP but I can't configure Network Manager to use the connection.

---

### Post by Bartender on 2011-04-18
Hi, frank!

I do remember you, and I still use the USB thumb drive you sent me!  Thanks for the link to the USB modem.  I'm glad you found something that works and it's cheap too.  My biggest question with these tiny USB modems is this - are they as "fast" as the US Robotics modems?  I feel pretty silly using the word "fast" in a discussion of dial-up modems, but you know what I mean.  The old US Robotics modems are robust devices that seem to cut through line interference better than other devices.  For instance, I have an old AOL dial-up modem that's about 2/3 as fast as my USR's.  To do a real-world test one would need to do some long-term comparisons from one location.  I know USR, Rosewill, and others are all building some version of these little USB modems that are supposed to work with Linux.

tboy5732, do you mean you've been trying to set things up so that you can use the modem via the Network Manager icon in the upper right corner of your screen?

Maybe things are different with the latest releases (I doubt it) but AFAIK dial-up users ignore NM.  I believe I remember using NM way back in Ubuntu 5.whatever but dial-up support went downhill.  Ever since then I've connected dozens of Ubuntu installs to my dial-up ISP (frys.com) by

1) plugging in a USR Sportster model external modem, 
2) using pppconfig to connect, 
3) reloading the package list via Synaptic (takes an hour or more on dial-up),
4) installing Gnome PPP

From there I've gotten into the habit of creating a Package Download Script (PDS) then finding some broadband with our Ubuntu-ized laptop and downloading the 200+MB of packages that always seem to be stacked up and waiting.  The laptop comes back home, the PDS goes onto a thumbdrive, thumbdrive to the PC stuck with dial-up, install.

There are a few details left out.  Now that the Archives have been closed my old dial-up threads that explained those details are gone.

---

### Post by frank cox on 2011-10-25
[QUOTE=Bartender;10690647]Hi, frank!

I do remember you, and I still use the USB thumb drive you sent me!  Thanks for the link to the USB modem.  I'm glad you found something that works and it's cheap too.  My biggest question with these tiny USB modems is this - are they as "fast" as the US Robotics modems?  I feel pretty silly using the word "fast" in a discussion of dial-up modems, but you know what I mean.  The old US Robotics modems are robust devices that seem to cut through line interference better than other devices.  For instance, I have an old AOL dial-up modem that's about 2/3 as fast as my USR's.  To do a real-world test one would need to do some long-term comparisons from one location.  I know USR, Rosewill, and others are all building some version of these little USB modems that are supposed to work with Linux.


Somehow I missed your reply , sorry. It appears I forgot to subscribe,dummy me !
 I will not say they are as good as a USR serial , but they seem as fast as any other winmodem.
If money was plentiful I would buy the USR serial USB for my laptop. E-bay has USR serial "ModemBlaster" modems for 20- 30.00 delivered and I have been pleased with them. 

I have no memory of sending you a flash drive , maybe if you described it?

Take care

---

### Post by ed bear on 2011-10-27
I see there have been a few new messages here, but no new ideas...

Figured I'd update the problem: still no success with GNOME-PPP.  I don't at the moment have a free machine with enough moxie to try an install of Lucid and then removing Network Manager, and I don't want to nuke this and have no net access to recover.

At the moment, interference from Network Manager seems the only surviving thing I know and have yet to try.  As noted above, I no trouble detecting and controlling the modem - everything works fine, dialing and connecting and delivering me the prompt.  For some reason, GNOME-PPP does not respond with user ID and/or password.

Network Manager - in Hardy - works fine, but I need to move up a version or two.  Hardy is now officially unsupported.  (But I'm not eager to switch to Unity!)
ED BEAR

---

### Post by _duncan_ on 2011-10-28
Fire up gnome-ppp and go to the settings or options screen. Can't recall the exact wording since I'm doing this from rote memory. This is the screen where you have a bunch of options to mark / unmark.

Make sure stupid mode is MARKED.
Make sure carrier check is UNMARKED.

Try dialing out again.

---

### Post by ed bear on 2011-10-31
First I should note that I didn't reply to Bartender's repeated stuff about reloading Synaptic and making download batches - that's because I've had it working all along.  My Hardy 8.04 system has been online and updated through Network Manager for years.  It's trying to switch to gnome-ppp so I can migrate to 10.4 that's been the rub.

Now, to _Duncan_:

I'd already tried "Stupid Mode." When I read your message, I did the following:

1. Disabled Network Manager by right-clicking its icon and unchecking the "enable networking" item.  I already know this does not interfere with dial-up using Network-Manager.  (I haven't figured out how to unload NM without removing it completely.)

2. Used ppp-config to uncheck Stupid Mode and Carrier Check, and verified the changes were saved.

3. Tested it again.

No luck, but a very different login log, readily repeatable:

=====
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*67,,,604-xxx-xxxx
--> Waiting for carrier.
ATM1L3DT*67,,,604-xxx-xxxx
CONNECT 44000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
=====

From this and the earlier logs, I think the dialer works just fine, but PPP is failing.  But that was clear previously, too.

The changes _Duncan_ sugested didn't get me as close as I did before, when I reached a login prompt but was unable to respond to it. Remember, the modem and computer and all work just fine on the exact same connection under Network Manager, which I am using now.  There is NO problem with identifying my modem or updating my systems.

ED BEAR
:confused:

---

### Post by _duncan_ on 2011-11-02
> **ed bear said:**
> 
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
=====


This is a common problem remedied by adding your user ID to the dip group, as follows:

```
sudo adduser [COLOR="Blue"]yourUserID[/COLOR] dip
```

> The changes _Duncan_ sugested didn't get me as close as I did before, when I reached a login prompt but was unable to respond to it. Remember, the modem and computer and all work just fine on the exact same connection under Network Manager, which I am using now. There is NO problem with identifying my modem or updating my systems.


The changes I suggested was meant to try to get past the login sequence once initial contact was made with the ISP (i.e. your last log). It has nothing to do with the permissions problem you encountered. It's difficult helping someone troubleshoot when other changes were being made to the system. Different error message, different solution.

I wish you good luck. Unsubscribing from this thread.

---

### Post by ed bear on 2011-11-02
Well, I guess _Duncan_ won't be reading this, as he's unsubscribed... I hope I didn't offend him by pointing to the things I'd already done.

I didn't make other changes to the system - just re-created the test situation I was in before, and added the changes he suggested (Stupid Mode and Check Carrier Line).  Undoing the changes returned me to the earlier log I posted, where I got to the login but failed CHAP.

I checked my groups and, yes, I'm a member of the following groups:
root
dialout    <===
dip        <===
users
libuuid
scanner
fuse
lpadmin
admin
ed-bear (of course)

However, I'm NOT a member of:
dhcp       <=== ???
syslog
klog
nvram
ssl-cert
crontab
mlocate
ssh
avahi-autoipd
gdm
pulse
pulse-access
pulse-rt
messagebus
avahi
netdev
polkituser
haldaemon
ntp

Now, DHCP might be a problem... I'll try that, too.

Bonus question: anyone know the command to display all the groups a user is member of? I just had to click through each one in the groups-settings window.  Couldn't figure out how to do it from a command line...

ED BEAR:confused:

---

### Post by ed bear on 2011-11-02
Well, adding myself to the dhcp group changed nothing.

I do note that my normal setup always dials twice (see <===****) but the changes _Duncan_ suggested resulted only in a single dialing, probably due to not checking the carier line.  Does this give anyone any ideas?

For clarity, here are three (consistently repeatable) logs, conducted with the same system and no re-boots.  Network Manager's connection as NOT started after starting up the system before testing.

For each test, settings were changed, gnpme-ppp closed and then re-opened to reload it and verify that the changes were saved, then connection attempted:

********** with CHECK CARRIER LINE=ON, STUPID MODE=OFF: **********
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*67,,,604-xxx-xxxx
--> Waiting for carrier.
ATM1L3DT*67,,,xxx-xxxx
CONNECT 44000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...    <===***
--> Sending: ATM1L3DT*67,,,604-xxx-xxxx
--> Waiting for carrier.
                          _
                         (_)
     _   _    ___     ____ __ ____    _  _____  _
    | \ | |  / \ \   / /_ | _/ ___|  / \|_   _|/ \
    |  \| | / _ \ \ / / | | | |  _  / _ \ | | / _ \
    | |\  |/ ___ \ V /  | | | |_| |/ ___ \| |/ ___ \
    |_| \_/_/   \_\_/  |__|__\____/_/   \_\_/_/   \_\
                 Authorized access only
   This system is property of Navigata Communications
Disconnect IMMEDIATELY if you are not an authorized user
     Contact xxxx@xxxxxxxxxxx for more information
User Access Verification
Username: 
Username: 
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT*67,,,604-xxx-xxxx
--> Waiting for carrier.
Username: 
Username: 
% Username:  timeout expired!
Username: 
% Username:  timeout expired!
Username: 
% Username:  timeout expired!
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATM1L3DT*67,,,604-xxx-xxxx
--> Waiting for carrier.
ATM1L3DT*67,,,604-xxx-xxxx

********** with CHECK CARRIER LINE=ON, STUPID MODE=ON: **********
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*67,,,604-681-1527
--> Waiting for carrier.
ATM1L3DT*67,,,604-681-1527
CONNECT 44000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

********** with CHECK CARRIER LINE=OFF, STUPID MODE=ON: **********
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*67,,,604-xxx-xxxx
--> Waiting for carrier.
ATM1L3DT*67,,,604-xxx-xxxx
CONNECT 44000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

ME AGAIN: Note that changing CHECK CARRIER LINE gave the exact same result I'd had with only STUPID MODE=ON.

Leaving STUPID MODE=OFF and CHECK CARRIER LINE=ON, the final permutation, got this latter log verbatim again.

Does anyone know how to configure a "PPPD Path" in wvdial?  I don't know what to point to, as config files are generated in several places.

ED BEAR

:(

---

### Post by frank cox on 2011-11-02
Hi Bear:

  I think you would do well to go with a later version, I have gotten dialup working in 11.04 . If you try using Gnome_PPP without Network manager  I think you will do better. If all else fails puppy linux is a no brainer w/ dialup!

 Here is some info I gleaned while making a cheap USB winmodem work in 11.04 . 
[http://ubuntuforums.org/showthread.php?t=1839620](http://ubuntuforums.org/showthread.php?t=1839620)  

When I looked at the errors in the Gnome-PPP log I had the same PPPD path error you did and the chap/pap errors, using the commands in the links below fixed them all save having to use sudo Gnome-PPP which was fixed by selecting 460800 as the speed.

Chap/pap secrets permission  error fix
[http://linmodems.technion.ac.il/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/archive-sixth/msg04656.html)

---

### Post by nashjc on 2011-12-03
Since last post is 4 weeks ago, this thread may have died. If not, I managed to work around the PPPD Path issue thanks to a post that suggested 

sudo nautilus

then find /usr/sbin/pppd and look at properties and change the checkbox to ON for "Allow executing file as program". 

This allowed me to get a connection just fine with gnome-ppp.

BUT ... (and if anyone knows answer I'd be very pleased), though my log shows a DNS etc., I cannot use browser etc. with my dialup connection. And, as others have noted, the dialup doesn't get into the Network Manager. Pain!

If anyone has ideas, please post. Even better, as I use multiple machines, offlist (I will post solution if one is found) to nashjc _at_ ncf.ca

JN

---

### Post by frank cox on 2011-12-03
As I said before, junk the network manager. it only works for broadband.
I have set up dialup in 9.4 , 10,4 , and 11,4 successfully and am about to do it in 12.4 .

---

### Post by roger_1960 on 2011-12-03
Hi

I tried for months with this and finally bought a USRobotics 5637 external USB dial up modem. I use it with gnome-ppp (dialer software from software center) and had to configure permissions as given below:

System settings
then
Users & groups
then
Advanced settings
then authenticate
User priviledges tab
Then tick "use modems" and "connect to internet using modem" - in fact tick them all!

Hope this helps

---

### Post by frank cox on 2011-12-03
> **roger_1960 said:**
> Hi

I tried for months with this and finally bought a USRobotics 5637 external USB dial up modem. I use it with gnome-ppp (dialer software from software center) and had to configure permissions as given below:

System settings
then
Users & groups
then
Advanced settings
then authenticate
User priviledges tab
Then tick "use modems" and "connect to internet using modem" - in fact tick them all!

Hope this helps

The USRobotics are good modems. I have been well pleased with my ancient 0839 USRobotics Soortster 33.6 fax modems flashed to 56k.
Also I have been well pleased with  a USRobotics  based serial modem ,The Modem Blaster, which  I bought on ebay for 20.00 delivered!
Fortunately I can use the internal modem on my old Gateway Tablet PC with Puppy Linux out of the box. For Ubuntu I use a dirt cheap USB Winmodem I bought on Ebay for 11.00 ! Those cheapies have worked on every Linux distro I ever tried them on. I am sure the USRobotics serial USB  you have is better than the cheapie USB winmodem but for 11.00 they work amazingly well.

One word of caution for those new to the fun of setting up dialup in Ubuntu most USB modems are winmodems and may be very difficult , if not practically impossible to setup. 

These USB winmodems do work very well and are only $11.00 delivered!
[http://www.ebay.com/itm/USB-56K-V-90-External-Dial-Up-PCI-Voice-Fax-Data-Modem-/160512097223?pt=PCC_Modems&hash=item255f443bc7](http://www.ebay.com/itm/USB-56K-V-90-External-Dial-Up-PCI-Voice-Fax-Data-Modem-/160512097223?pt=PCC_Modems&hash=item255f443bc7)

I am sure there are others but experimenting is expensive!

These external serial modems work very well , probablly the best buy in a serial modem anywhere!

[http://www.ebay.com/itm/NEW-Creative-Blaster-V-90-Modem-56k-retail-box-/120822122183?pt=PCC_Modems&hash=item1c218f46c7](http://www.ebay.com/itm/NEW-Creative-Blaster-V-90-Modem-56k-retail-box-/120822122183?pt=PCC_Modems&hash=item1c218f46c7)

You can buy an old USRobotics serial modem for anywhere from 10.00 to whatever.  These are very good modems despite their age . They were designed for mission critical dialup operations and are super reliable and maintain the connection as well as can be. Any new commercial external serial modem  from US Robotice will be a good machine and it is supposedly possible to make the fax work in Linux but I never tried.
Using the drivers from Linmodems is a waste and if they do not work good luck getting a refund! 
Do not waste your time ! Many Dell modems have a free full speed driver available and I have made them work . My advice from my limited {3 years } of using Linux is the easiest and best choice is to use Puppy Linux on older equipment, 60% of the time the internal winmodem will just work .It's super fast even with 256k of ram.

If the machine is stationary buy an external serial modem . A cheap external serial is better than any winmodem and far easier to setup . For no more than the linmodem driver you can buy a first rate serial!

If money is an issue and you need portability  (see laptop}  the cheapie USB winmodems on ebay are surpassingly easy to setup and the connection  is not half bad

---

