---
title: "Dial Up Connection Problem"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Twitch04 on 2009-12-26
Hello, everyone. 

I'm a dial-up user [fun fun, I know] who is trying out Ubuntu 9.10 [full yupdated] by dual-booting it with Windows XP, which is what I'm running at the moment. I managed to get Linux drivers for my modem, so that was good. My friend [who turned me on to Ubuntu and Linux in general] told me to be careful, for Linux and dial-up don't have a very wonderful history together.

Now my problem is trying to connect to the internet itself, of course.

I've tried Knet, wvdial, and gnope-ppp, but most of them freeze [the computer doesn't freeze, just all progress stops] at the pppd phase. 

The terminal tells me, when gnome-ppp runs at least- that the password I send is bad, so it drops the connection as soon as it's dialed. I'm running it via the terminal [sudo gnome-ppp] so that I have all permissions when I do it.

I should also say that on XP I use the AOL dialer, since... well... it's how we connect here. I did some research and saw there used to be a PengAOL thing, but that was in 2006 and I couldn't find a download, much less believe that it's still supported or usable.

If there is any other information I'm missing, feel free to point it out and I'll tell you if I can.

Thanks in advance!

---

### Post by GeorgeVita on 2009-12-27
Hi **Twitch04**, please post more data to check:

a. post contents of /etc/wvdial.conf
b. try to connect using sudo wvdial ... (any command you are using)  and post ALL terminal contents including your typed command. If 'frozen' press CTRL-C one or two times

Regards,
George

---

### Post by Twitch04 on 2009-12-27
Thank you for replying, George.

Here is the contents of /etc/wvdial.conf. I had already previously edited it when I was trying to use wvdial, but it didn't work. Took me a sec to figure out how, but I had to navigate there in the terminal and do sudo gedit wvdial.conf, or something like that, because I didn't have permission to edit it.

 > [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/modem
ISDN = 0
; Phone = 269-823-0038
; Password = herp derp
; Username = haha





  The username and password are actually there; they're what I use to connect to the AOL Dialer in Windows, and that phone number is the number that the AOL dialer dials. I thought that to connect to an AOL Dialer number, I'd have to use the username and password that I use.

Here's the terminal stuff:



 > ben@jewstation:~$ sudo wvdial
[sudo] password for ben: 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
ben@jewstation:~$ 


 
  

---

### Post by GeorgeVita on 2009-12-27
Hi **Twitch04**, edit /etc/wvdial.conf:

```
gksudo gedit /etc/wvdial.conf
``` remove semicolons from the last 3 lines & add an extra line: ```
Stupid mode = yes
``` Retry and post your progress.

If your username/password is exact as your previous post, edit that post, delete them and change your real password after connecting to your provider. 

Regards,
George

---

### Post by Twitch04 on 2009-12-27
Haha... Yeah, oops. XD. Wasn't thinking there. 

Anyway, this is what /etc/wvdial.conf looks like now:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/modem
ISDN = 0
  Phone = 1-269-823-0038
  Password = [My Password]
  Username = [My Username]
Stupid mode = yes

```I put the 1- at the front of the number. I don't think it matters since the area code's the same, but... I did. And I didn't know if I was to keep the spaces there or not. I took away the spaces, too, the first time, but leaving them there seemed to be more effective. It got... it seemed like it got further along. But this is what the terminal shows now:

```
    [FONT=&quot]ben@jewstation:~$ sudo gedit /etc/wvdial.conf
[sudo] password for ben: 
ben@jewstation:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT1-269-823-0038
--> Waiting for carrier.
ATDT1-269-823-0038
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Dec 27 15:12:59 2009
--> Pid of pppd: 2086
--> Using interface ppp0
--> pppd: pXB[08]@_B[08]
--> pppd: pXB[08]@_B[08]
--> pppd: pXB[08]@_B[08]
--> pppd: pXB[08]@_B[08]
--> pppd: pXB[08]@_B[08]
--> Disconnecting at Sun Dec 27 15:13:00 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
[/FONT]
  [FONT=&quot]
[/FONT]
  
```It looks like the problem is with the account and/or password... but I don't know why, really. I don't know what all the "pppd: pXB[08]@_B[08]" stuff is.

And, just curiosity, what does enabling this "stupid mode" do? And the "gksudo"? Or at least the "gk" in it.

---

### Post by GeorgeVita on 2009-12-27
These are non printable characters for the terminal window, do not bother.

You must be sure about your username and password (can you check them with other working connection?) and retry.

**EDIT: also it is better to remove dashes from dial number**

Usually 'old' dial-up providers were sending a 'login prompt' for manual typing. This mode (assumed to be a stupid one for 21st century) is bypassed with this parameter. More about all parameters for wvdial/pppd using the terminal commands:

man pppd
man wvdial
man wvdial.conf

G

---

### Post by Twitch04 on 2009-12-27
Yeah, they're the username and password that I use with the AOL Dialer in XP... which I'm running right this very moment, haha. So yes, they're definitely correct.

But alright. I'll do those 3 things and check back in in a few minutes. Rebooting into Ubuntu and back into XP and back and forth has become quite a common activity in the past 24 hours, haha.

---

### Post by GeorgeVita on 2009-12-27
"On/off topic note": after using Ubuntu for some months, my dual/triple boot became Ubuntu 9.04 / Ubuntu 9.10 / PuppyLinux ...

extra page for reference: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

from **man pppd** exit code = 19 means
' 19     We failed to authenticate ourselves to the peer.'

I do not know if your provider needs extra parameters or a specific method to authenticate. If this is the reason we need EXTRA help from other readers!

G

---

### Post by Twitch04 on 2009-12-27
Alright, things have changed a little bit. 

Just earlier, we ordered and downloaded the software to connect to the internet with AT&T, NOT AOL. I did some research, and AOL only allows you to connect by using THEIR software. The only alternative is PengAOL, which I couldn't get working. The guide for installing it was on an older version of Ubuntu that compiled things differently and... it wasn't pretty. 

So now we have AT&T, since that's who we pay for our phone service anyway. I tried the new number with the ID and password that we registered and it still didn't work with gnome-ppp [still said bad username/password pair], but I only tried it once and didn't explore my options since I had to return to Windows fairly quickly.

Googling told me [actually through another thread on the Ubuntu forums] that AT&T does work, for sure. So at least I don't have to worry about that. But I'll work on it more later and report back here. Hopefully I can get it to work, now, by SOME method.

---

### Post by Twitch04 on 2009-12-28
[I don't know if double-posting is frowned upon here, but there's been a new complication]

For some reason, Ubuntu has decided that it can not find my modem again. I already went and did the scanModem thing and got the correct drivers before I even made this topic, and those drivers are still installed. But in Knet, it can't find my modem when I click "Scan Modems," gnome-ppp can't find it using "Detect," but if I run scanModem again it can still find my modem, just like before. 

I'm so confused. What could cause this, and how can I fix it? Because having new numbers and service is useless if Linux doesn't think I have a modem.

---

### Post by GeorgeVita on 2009-12-28
Hi **Twitch04**,
the only possible reason is a running or 'hanged' program 'holds' the communication port /dev/modem (like wvdial trying to connect).

You have to find a repeatable working procedure and continue from that stable point for further tests. You can check system activity with terminal command: **dmesg**

Review your steps regarding [driver]("https://help.ubuntu.com/community/DialupModemHowto") 

'double-posting' may trigger new ideas and 'no-post' could mean no more ideas!

>>> Dialup expert into ubuntuforums.org is [ikraemer]("http://ubuntuforums.org/member.php?u=365139")
>>> try a search within [his posts]("http://ubuntuforums.org/search.php?searchid=68567658")

Regards,
George

---

### Post by Twitch04 on 2009-12-28
But wouldn't it say that the modem is busy? Not that it's not there at all?

And after a system reboot, there shouldn't be any random programs that are "hanged," right? 

I just don't see why it would detect it and then suddenly... well... not detect it. haha.

I'll do some more investigating today with my Linux friend, too, and return.

---

### Post by lkraemer on 2010-01-04
While I haven't tried wvdial on Ubuntu 9.10 the steps should be
pretty well the same as 8.04.3 LTS. Some Directories or Files might
have their contents changed.  We'll find those with your help.......

For now just stick with wvdial and pppd until we have more information.
Too many software packages, and mixing and matching causes lots more
headaches.  Once it is working switch to Gnome-PPP.

As of now you should know your ISP Dialup telephone number, userlogin,
and userpassword, because it is working in Windows.  Add that information
to the wvdial.conf file.

In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you will need to add a few things...
like Phone, Password, Username, and your modem type
and Init strings might be slightly different from mine
as shown below.......)

wvdial.conf should contain something like this......:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net
[code]

You will need to set up the pap-secrets and/or chap-secrets file by running
the following in a Terminal Window (Try PAP First):
[code]
sudo pppconfig

```

You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configuration and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppdconfig

```

pap-secrets file contains:
(NOTE: File Format has changed for versions later than 8.04)
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourusername@yourisp.net" provider "yourpassword"

```

Now assuming that your pap-secrets and/or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
(if that doesn't work try:)
```

sudo wvdial /etc/wvdial.conf

```
You may not have to do the following step.....but 8.04.3 LTS requires it.
To enable dialout without Root permission do:
```

sudo chmod a+x /usr/sbin/pppd

```

You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications and
compare Windows sounds with Ubuntu as the connection progresses.
If your config files are correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to terminate
the session when you are done, BUT FOR THIS SESSION YOU MUST LEAVE THE
TERMINAL WINDOW OPEN...) You may have to uncheck the box marked OFFLINE
when you open your browser to make it go ONLINE. Surf, then terminate the
open session with CNTL C in the open terminal window where you initiated wvdial.

If wvdial dials out and transfers to ppp and the connection then drops the problem
is an incorrect configuration for pppd.

Finally, when wvdial is working you can configure/set up Gnome-PPP.

When you get everything working, I'd suggest backing up the pap-secrets,
chap-secrets, and wvdial.conf files....just in case.
You can use:
```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

```
to save the backup files.

So, now you have lots of things to check and try....

What town in MI?  I was stationed at Wurtsmith AFB, Oscoda, MI from 1972 until July 31, 1975?

lk

---

