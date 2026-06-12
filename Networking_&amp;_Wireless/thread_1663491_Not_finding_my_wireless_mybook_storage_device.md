---
title: "Not finding my wireless mybook storage device"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by Cleanville on 2011-01-09
This question is so basic, maybe it should be in "Absolute Beginners," but here goes:

I have a Western Digtal MyBook storage device connected to my router.  I have used this to wirelessly store and serve data files for the past couple of years to all the windows computers in my house.  Now I have added an UBUNTU computer to the mix.

In Places -> Network:  a "windows network" shows up.

when I open this "windows network" by clicking its icon, an empty window shows up.

Questions:

is it possible for my UBUNTU computer to see this drive?

if so, is it possible for the UBUNTU computer to read data that the windows computers have put on this drive over the past couple years?

---

### Post by PatchesTheCaveman on 2011-01-10
Try connecting to it manually via its IP address.  To do so, go to Places > Connect to Server in your top menu.  Change *Service type* to **Windows share**, put its IP address in the *Server*, and click *Connect*.

If you don't know the network attached storage device's IP address, check its configuration, the DHCP clients list in your router configuration if you have access to it, or figure out its name on one of the Windows computers and open a command prompt on that Windows computer and run:
```
ping *<name>*
```
It will output something like:
```
PING nas-drive (192.168.1.10) 56(84) bytes of data.
```
Your storage device's IP address would be 192.168.1.10 in that case.

---

### Post by Cleanville on 2011-01-11
I have apparently made some progress.  i can now "see" the network storage device, but it says:

Unable to mount location
Failed to retrieve share list


btw, nothing new showing up in "additional drivers"

---

### Post by PatchesTheCaveman on 2011-01-12
Figure out its name from that screen and go to Applications > Accessories > Terminal and type the following and press Enter:
```
smbclient -L -U guest //*<name>*/
```
Just press Enter when it ask's for *guest*'s password.  Then copy and paste the output into a reply to this thread.

---

### Post by Cleanville on 2011-01-13
> **PatchesTheCaveman said:**
> Figure out its name from that screen and go to Applications > Accessories > Terminal and type the following and press Enter:
```
smbclient -L -U guest //*<name>*/
```Just press Enter when it ask's for *guest*'s password.  Then copy and paste the output into a reply to this thread.

guest: Not enough '\' characters in service
Usage: smbclient [-?EgBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-p|--port=PORT] [-g|--grepable] [-B|--browse]
        [-d|--debuglevel=DEBUGLEVEL] [-s|--configfile=CONFIGFILE]
        [-l|--log-basename=LOGFILEBASE] [-V|--version]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] service <password>

---

### Post by thefix0r on 2011-01-13
A wireless NAS, what an absurd concept, connect a cat5 cable, what, are you planning to juggle your terabyte drives?

---

### Post by Cleanville on 2011-01-13
> **thefix0r said:**
> A wireless NAS, what an absurd concept, connect a cat5 cable, what, are you planning to juggle your terabyte drives?

Not sure what an NAS is, although the term seems to come up on these threads a lot.

I wanted to wirelessly share my terrabyte drive, if feasible because it has 30,000 or so mp3s and I am constantly acquiring new ones through the two windows machines I have going.  However, if it is not feasible to do this, I can understand that and it won't bum me out too bad.

Side note:  I am exploring LINUX because I have used a text-to-speech automatic dj for many years on my windows machine to announce songs before and after they played in WINAMP.  This feeds my house-wide fm station so that I can hear the music on radios placed all over my house.  However, newer windows machines won't support the old text-to-speech dj (or any text-to-speech dj).  Seem to be running into a similar problem with LINUX in that there was a text-to-speech auto dj circa 2005, but that is difficult to resurrect here in 2011.

---

### Post by PatchesTheCaveman on 2011-01-14
The fact that your device is wireless does not contribute to your particular problem.  You could very well experience the same problem with a similar wired device.  NAS stands for network attached storage, which refers to any device dedicated to making a disk available on a network.

I fubared on that last command last time.  My apologies.  Try:
```
smbclient -U guest -L *<name>*
```

---

