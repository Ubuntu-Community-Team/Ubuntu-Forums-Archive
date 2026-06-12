---
title: "[SOLVED] Wireless won't reconnect when dropped."
date: 2008-01-07
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-01-07
I have two machines running Ubuntu. One is running Feisty Fawn and the other is Mythbuntu which naturally would be Gutsy.

Both machines are using the same make and model wireless network card.  The machine running Feisty will reconnect to the network if it goes down but my mythbuntu box won't.

If I ever have to reboot my router I subsequently have to reboot my mythbuntu box to get it back on the network.  I've also come to find that if I don't reboot the mythbuntu box in a timely manner it will eventually crash and require a reboot anyway.

Is there a way to tell my myth box to reconnect after it has lost its connection?

I saw in a different post that there was a command, something like /etc/init.d/networking restart  

I had tried it once but it said that networking wasn't a valid command.

---

### Post by Meph1st0 on 2008-01-12
Okay, here's another idea.  If my pc happens to drop off the network.  Is it possible to configure one of the buttons on my remote to run a script that will reboot my machine?  some sort of script that includes: sudo shutdown -r now
But also include the sudo password so that I don't have to whip out the keyboard just to get to reboot.  Though that posses a security threat there, I don't want to have my sudo password sitting in a text file somewhere on my computer.

---

### Post by rusty0101 on 2008-01-13
for restarting your network, use the command:
```

sudo /etc/init.d/networking restart

```

You'll be prompted for your password.

likewise to reboot, the shorthand command is:
```

sudo reboot

```

As I understand it, you can add such a command to the MythTV front end. I know it's been done under Knopmyth, but I don't recall all the specifics. Basically the menus for MythTV are .xml formated files, so adding a reboot or shutdown command is possible, but I don't recall the syntax, or where it should be put.

One of the features of sudo is that you can define certain commands that can be run without being prompted for a password. To attach it to a button on your remote (I would suggest a confirmation stage actually) you would want to edit your ~/.mythtv/lircrc file and find the appropriate button and modify the 'config' line for that button. You may have to edit multiple instances of the button for the various applications involved. i.e. you might want some applications to exit rather than reboot the computer. I haven't tried that capability, but it is definately possible. You can also use a combination of a keymap file and lircrc to do that.

Hope this helps.

-Rusty

---

### Post by faginbagin on 2008-01-13
Hi Jonathan,

First, I think you should figure out why your box is crashing, that doesn't sound good.

Second, I was having trouble losing my wireless connection to the network and hated not being able to use ssh to get it. What I did was write a litle shell script that runs as a cron job every 10 minutes. It uses wget to check the connection. If it succeeds, great. If not, it calls ifdown, followed by ifup, plus some iwconfigs before & after. All output is piped into sendmail (actually exim4) so next time I log in, I'll know when there was a problem. I use mailx on the myth box to read it.

Here's the shell script:
```

# Crontab entry:
# 5,15,25,35,45,55 * * * * /home/mylogin/bin/checkWiFi

IFACE=rausb0

wget -q -O /dev/null "http://www.google.com" || (

echo "Subject: Connection down?

Output from wget:"
wget -O /dev/null "http://www.google.com" || (

echo "Output from iwconfig/ifdown/ifup/iwconfig"
/sbin/iwconfig $IFACE
/sbin/ifdown $IFACE
/sbin/ifup $IFACE
/sbin/iwconfig $IFACE

)

) 2>&1 | /usr/sbin/sendmail mylogin


```

Paste the above into /home/mylogin/bin/checkWiFi, make it executable, then copy the second line into another file, e.g. mycron. In mycron, remove the leading hash mark and space.

You will probably need to change the value of $IFACE. If you don't know the name, iwconfig should tell you the name of your wireless interface.

As root, run the script from the command line to make sure it works as intended.

To make it a cron job, as root, execute the command:
crontab mycron
To make sure the command took effect, execute:
crontab -l
This should print out that single line.

HTH

---

### Post by Meph1st0 on 2008-01-15
great!  thanks for the suggestions.  I'm going to give them a try!

---

### Post by michwill on 2008-09-25
I'm having the same issue, but instead of checking to see whether or not it's connected, I simply set up a root cron job for every 30 minutes that restarts the network.  Although I can do it manually as I please, the cron job never works.  Syslog says the following:

```

There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072

```

I have wireless laptops, towers, and printers, and they all work fine.  The Mythbuntu box is the only one that doesn't reconnect.  My questions are:

1) Why in the world does my wireless keep dropping?
2) Why doesn't the cron job work when running it manually runs just fine?


NOTE: My wireless adapter is an ENUWI-G2 ([http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=293](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=293)).  Mythbuntu recognized the adapter natively, but I decided to use NDISWRAPPER with the XP driver after noticing the issues -- it performs the same.


Regards,
Michael

---

### Post by faginbagin on 2008-09-25
Hi Machael,

> 1) Why in the world does my wireless keep dropping

Dunno.

> 2) Why doesn't the cron job work when running it manually runs just fine?

Are you running both as root? Have you checked email for the account? Unless the cron job is redirecting to /dev/null, you should get any stdout, stderr messages sent to the cron job user as email. That can help trouble shoot issues, like different PATH and other environment variables used by cron jobs vs login shells.

If the above ideas don't help you solve the problem, can you post the cron job entry and script?

HTH

---

### Post by michwill on 2008-09-29
Where is email sent to root?  I wasn't aware that Mythbuntu set up a mail subsystem.

---

### Post by faginbagin on 2008-09-29
FWIW, I didn't install the mythbuntu distro. I installed Ubuntu 7.10 and then installed myth-control-centre from mythbuntu. I didn't know about the mythbuntu at the time.

I just took a look and I see that the cron package doesn't require, but does recommend a mail package. I happen to have exim4 installed. I vaguely remember configuring it so that email meant for root is sent to the account I normally use to login. I think I had to explicitly install an MUA (mail user agent, AKA mail reader). I chose the rather basic mailx. And I do get email meant for root as well as email when the script I posted detects a problem with my wireless connection. /usr/sbin/sendmail is provided by the exim4 package.

If you don't have a mail package like exim4, maybe cron logs something in /var/log that you can examine? And you can probably install exim4 if you can't find where error messages from cron jobs go.

HTH

---

