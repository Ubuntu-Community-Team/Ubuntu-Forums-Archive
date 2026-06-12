---
title: "Problem with UMW190 USB Modem (Verizon Wireless) and Ubuntu 9.04"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by aquante on 2009-09-18
Hello,
I am new to forums, so hopefully I am at the right spot to ask my question.  I have an ASUS EEE PC netbook that I have installed Ubuntu 9.04 to.  

Everything works flawlessly except for my USB Modem.  I try using the Network Manager (easiest thing first) and it tries to connect but says that the "GSM Network Disconnected".  While VZW is CDMA, this modem does have a SIM card in it and is a world modem that could theoretically be used on GSM.  I am attempting to use it in the US on CDMA, however.

The settings I have for Network Manager are the following:

Number: #777
Username: <my ten digit phone #>@vzw3g.com
Password: vzw

I have none of the advanced fields filled out.  On the PPP Settings tab, I have the following:

Allowed Methods: EAP,PAP,CHAP,MSCHAPv2, MSCHAP

Allow BSD data compression, Allow Deflate data compression, and Use TCP header compression are all checked.  The other boxes are unchecked.

In the IPv4 Settings tab, the method is simply set to Automatic (PPP).

I've also tried connecting through Gnome PPP, I've tried using the PPP dialer from the command line (the name of it escapes me at the moment).  I've also tried simply installing WINE and grabbing the Windows version of VZ Access Manager.  VZ Access Manager installs with no problem, but it will not detect my USB Modem at all.

I'm willing to try virtually any method (no matter how complex) to get this working.  I can provide whatever logs or do whatever additional commands that are needed to provide more information.  

I appreciate your time and help!
Alex

---

### Post by johneh on 2009-09-18
Hi Alex
 

 I have a HUAWEI E169 3G modem, in which I had connection problems.
  My work around was, no user name or password. You will need your authentication access  number i.e.  #777 and your APN, you may have to change the Ipv4 settings to automatic (ppp)  address only and add the dns server numbers
 This method got me up and running.
 All the above information was obtained  by installing the wireless modem on a windows xp computer, then using the connection software to pick out the necessary info, or speak to your isp.   
 Good luck
 

 John.........

---

### Post by aquante on 2009-09-18
Hi John - 
Thanks for your response.  I know that I did try connecting with the Network Manager without my username/password and it did not work.  I'm not sure what the APN actually is or how to obtain it?

I'll try your other suggestions regarding the DNS server names, etc and see where that takes me...

Thanks!

---

### Post by aquante on 2009-09-19
Hmm, that didn't seem to work.  I grabbed the DNS server IP addresses from when it was connected in Windows and popped them in there.  I blanked out the password/username.  The only part I didn't do was the APN because I didn't know where to find that or what it was.  Based on searching for it on the web, I get the impression that Verizon Wireless doesn't use an APN?

Not sure if you have any other suggestions, but I appreciate you trying...

---

### Post by johneh on 2009-09-19
Hi Alex

try this 

Access Point name: vzw3g
Username: <mobile#>@vzw3g.com
Password: vzw
Dialup: #777
use DHCP-auto and DNS-auto

again good luck

John.........

---

### Post by aquante on 2009-09-20
Hi John - 
Thanks for all of your help.. with some additional trial-and-error, I finally got it working.  It's not the most elegant method, but it serves the purpose.

I basically followed the following config files in this article: [http://www.linux.com/archive/feature/52729](http://www.linux.com/archive/feature/52729)

I used their pppd and chatscript and I can now connect via the pppd dial command in the terminal.  The only that I noticed that is odd (to me, at least) is that the device name changes sometimes when I plug into the USB port.  Sometimes it's ACM0, othertimes it's ACM1, ACM2, or ACM3.  So, I have to go and edit the config file accordingly if that occurs.  It's a bit clunky to have to do that, but hey - it works! :) 

Thanks again for your help!
Alex

---

### Post by exploreRPG on 2009-09-24
I am also having this problem. I recently got this modem when my aircard broke. Now I can't seem to connect at all. It insists I am connecting GSM when I use #777.

On the windows side, there is a option to control the network. The setting defaults to Global even when I change it to CDMA. (It still works under Windows, so I imagine there is something else going on.)

Tye

---

### Post by aquante on 2009-09-24
> I am also having this problem. I recently got this modem when my aircard broke. Now I can't seem to connect at all. It insists I am connecting GSM when I use #777.

On the windows side, there is a option to control the network. The setting defaults to Global even when I change it to CDMA. (It still works under Windows, so I imagine there is something else going on.)

Tye 	

Hi Tye - 
Did you try this link?  [http://www.linux.com/archive/feature/52729](http://www.linux.com/archive/feature/52729)

Basically, I just created the two scripts contained within that article.  After that, I was able to connect with the "pppd call <config file name>" command (without quotes, of course) and it worked.  You can tail -f /var/log/messages to see that it's connecting.  The key thing to look for is that it assigns you IP addresses, that's indicates that you're connected.

Hope that helps!
Alex

---

### Post by exploreRPG on 2009-09-24
I tried, but it didn't work.. maybe I typed something in wrong.  I am getting this in the trail.

pppd started by root, uid 0
Exit.

When I plug in the UMW190 it detects the modem, but sets it up as a GSM instead of CDMA. I change the dialup settings but it still thinks its GSM. 

Question: 

What are these fields:

APN:
Network:

PIN:
PUK:

When I used the USB760 these fields never appeared. I was able to connect immediately.. I can't figure out why its insisting the connection is GSM and I'm not getting any clear information were system files are located. (very cryptic.)

BTW, this is a *fresh* ubuntu install 9.04 on a Fujitsu Lifebook u820. (Only thing I have done is enabled the touch screen drivers.) - Can't get any further if I can't connect to the internet for updates/modules.

:/

---

### Post by exploreRPG on 2009-09-24
OK.. I got connected.. but let me tell you those scripts are not very clear. After examining them, I figured out the goal, Its sending Hayes commands to the modem in a format of <expected> <send>  After refreshing my memory on the old-tech. hehe here are the scripts I created.

```

TIMEOUT 20
ECHO OFF
ABORT '\nNO CARRIER\r'
ABORT '\nERROR\r'
ABORT '\nNO DIALTONE\r' 
ABORT '\nBUSY\r' 
ABORT '\nNO ANSWER\r'
'' \rAT
TIMEOUT 60
OK ATH0
OK ATQ0
OK ATV1
OK ATM1
OK ATS0=0
OK ATS7=60
OK ATDT#777
CONNECT \d\c

```

I separated the commands out so the tail would show if each were accepted. It works and I am posting this via my Lifebook. The network manage doesn't acknowledge this connect. How can we fix this?

What is the dialup connection manager doing to force a GSM connection? (changing the dialup #) ?

---

### Post by aquante on 2009-09-24
Congrats on getting online with the modem!  I'm not sure how to get the Network Manager to get it to recognize it properly.  When I connect via the pppd call command, it doesn't change the status on Network Manager at all.

When I connect, I just leave the tail -f /var/log/messages running in the term window and minimize it.  If I experience any issues with being disconnected, it's reflected in that log.  This method was the only way I could get this modem to work.

I had previously tried using the Network Manager, KPPP, Gnome PPP, and wvdial and had no luck.  Fortunately, I only use this connection on my Netbook and it's not anything that is mission critical.  Otherwise, I'd probably attempt to work further on making it work for KPPP or something that had a GUI of some sort.

---

### Post by exploreRPG on 2009-09-24
Well it seems like this is an old error that has resurface.. I am connected and I closed all windows.. I will see how long it lasts..

This issue was originally posted / fixed.. 
[https://bugs.launchpad.net/ubuntu/+source/libmbca/+bug/290625](https://bugs.launchpad.net/ubuntu/+source/libmbca/+bug/290625)

I would like to know more about how this connection manager works.. I am a professional c developer but don't reall understand all the modules or a naming convention within linux. (it all seems jumbled together.)

(ie folders called 10freedesktops\ etc. seems like the OS isnt well organized.)

---

### Post by exploreRPG on 2009-09-24
Correction.. This doesnt hold a connection.. :(

This script shows that it works, but I never put my PW in the script.. I was wondering how the connection would hold.

(not a good solution..)

Tye

---

### Post by aquante on 2009-09-24
Yeah - I think you have to leave the terminal window open in order for it stay connected.  I believe that by closing the term window you're also killing any processes launched while in that term window.  

I know some C/C++ also from my college time, but I am really rusty since I don't use it regularly - I'm more of a Perl/PHP guy these days.  

When I was trying to make the modem work in Network Manager, I even removed the simcard from it temporarily in hopes that it would quit thinking that I want to connect on GSM, but no dice.

---

### Post by exploreRPG on 2009-09-24
I tried that too.. Can you direct me to the source module? Or someone who actually works on the ubuntu source?

I was very excited when my USB760 worked immediately, but this is a deal breaker and I'll be forced back to Vista/XP if I can't resolve this.

:(

---

### Post by aquante on 2009-09-24
Unfortunately, I don't know the answer regarding the location of the source code.  I'm just a regular old Ubuntu user, not a developer or anything.   I'm actually kind of new to Ubuntu - I work on Unix machines for my job, but never really dabbled at home with Linux/Unix until recently.

If you do happen to find out how to contact a developer, I'd love to know as well...

---

### Post by rvndrk3233 on 2009-11-04
from my understanding of the core code:

we have hw detection on PCI bus to detect tty modem.
the wvdial would work to some extent, thanks to point that out previously. I kept getting access denied when using ttyXXX, even as root, as device was in use.

from there, the usb device and bus takes over.

check the drivers core under serial modems.The kernel code is rough at best.

I work on FPOS and am having love/hate relationships with the innefficient C devs on the kernel team.I too am looking, but no module seems be loading up.

The UI for this is like it was back in 8.04 with wifi cards.Spotty at best until someone figures out how it works.

Thanks for the tip, but I think, the card needs password and username fields in the dialing script to maintain your 3g, literally (3-gigabit,level 3), connection.Notice all cards of this type dial #777.It not limited to verizon, ntelos cards dont unmount in linux and mine has serious flaws anyway so Im not using it.

The UI poorly attempts to configure all modems, but it does try, Ill give you that.

 Personally, Ive written better comm port code, but everything with linux/ubuntu is wrapped so many different ways from tuesday, its hard to see clearly what code does what.Hence my attempts to try and RE-write UNIX/Linux. So far, I'm succeeding, but no filesystem yet.
Im close to an initial Ram disk.

As for Ubuntu users, keep pluggin away, some will get it, some wont until the devs make a module for us. ATI video chipsets were like that a ways back.It was hit or miss.

So far, I'm missing.I have this exact card.Could really use ubuntu right now.

---

### Post by rvndrk3233 on 2009-11-04
Good news!! I have tested and I can connect.

Here is what I did:

Use the two files on the first link given.You have to create the files with sudo nano /etc/ppp/peers/<filename>

chown to <me> , not really necessary, but it helps.
chmod 777 <filename> , both of them.NEEDED. I used the wildcard '*'.

sudo ppp (wont work as non-root user) dial 1xevdo (which is the name of the script)

NOTE:
The tty device listed as ACM in the first script MUST be the second one listed in the /dev folder. Do a 'ls /dev/tty*' to see the list.So, if you get a USB hiccup or disconnect, you HAVE to increment the file.

Still have no way of a polite disconnect yet.

You know if you are connected about 5-10 seconds later if you try and ping or traceroute out and it waits a second or two to reply back.

But you will CONNECT using this setup. Another BUUN to Ubuntu. Now I can kick this nasty OSX habit I have.  :-)

---

### Post by akshunj on 2010-02-09
So, Jaunty and Karmic still have this bug.  Sucks.  The scripts mention above work using "sudo pppd call 1xevdo".  However, I needed to edit the 1xevdo_chat script to remove the ABORT 'no dialtone' command.  It made the script error out every time I tried to connect.

--Akshun J

---

### Post by fheinsen on 2010-03-19
I just posted an all-GUI solution here:
[http://ubuntuforums.org/showpost.php?p=8996651&postcount=2](http://ubuntuforums.org/showpost.php?p=8996651&postcount=2)

---

