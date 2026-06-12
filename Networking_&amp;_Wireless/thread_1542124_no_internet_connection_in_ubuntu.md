---
title: "no internet connection in ubuntu"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by razor180 on 2010-07-30
I have no internet connection in ubuntu.
 
what happened is I installed openSUSE 11.3 (which I am now regretting) and it killed the internet connection in ALL of my operating systems (I know it was openSUSE because it was the only thing that changed), that includes windows and linux mint. so I installed ubuntu (for multiple reasons, one I thought it might redo the connection errors that openSUSE caused and two, openSUSE's grub only allowed me to connect to openSUSE and windows). I got rid of openSUSE when I installed ubuntu. Now, for some inexplicable reason, windows' internet connection is working again, yet it is the only OS on my PC that has an internet connection, ubuntu has none and neither does linux mint or openartist (all ubuntu derivatives).
 
anyways, that's how I got into this problem (this time, I seem to be running into problems left and right lol)
 
I have the network manager set to eth0 (it's a desktop) and I have eth0 set to automatically find the DHCP and have the IPv6 set to automatic as well
 
I have my desktop connected directly to a wireless router via an ethernet cable (and the router is obviously connected to the modem) if that helps at all
 
thanks for the help in advance

---

### Post by marc.verwerft on 2010-07-30
Have you looked already in dmesg/syslog etc. for suspicious lines?

Have you tried a live CD/USB version of ubuntu/knoppix/mint?

What type of PC is this?

---

### Post by razor180 on 2010-07-30
like I said, it's a desktop with a direct ethernet connection that goes through the ethernet ports on the wireless router (I'm using a laptop right now so I can be on the forums without having to switch constantly on my desktop between ubuntu and windows)
 
I built it myself
the motherboard I used sometimes has some problems with linux connectivity as the drivers for the integrated ethernet card aren't great
it's an ASUS m4a79xtd evo
 
dmesg didn't pull up anything useful and I don't have syslog, apparently you have to download a package for it, it doesn't come with ubuntu upon install
 
yes I have, I was having the same no connection problem through a live disc before I installed ubuntu, BUT, there were multiple reasons I dismissed that, one, I thought it was because the problem presented by openSUSE was still there and I needed to install to fix it (not sure if it worked, but after restarting I got windows' connection up) and I have had connection problems with live discs before that went away upon install
 
and yes, this is a fresh install of ubuntu

---

### Post by marc.verwerft on 2010-07-30
Sorry forgot to specify that dmesg is a command and syslog is a file.

You can find it under /var/log/ and open it with any editor though I recommend using 'System/Administration/Log file viewer' There you have access to all log files (syslog, daemon.log, messages, ...) etc.

The reason I asked your type of PC is because your problem might be related to your BIOS - see also [http://ubuntuforums.org/archive/index.php/t-1465703.html](http://ubuntuforums.org/archive/index.php/t-1465703.html)

Hop this helps

Marc

---

### Post by razor180 on 2010-07-30
+3well, thing is, this problem hasn't been persistent until now, and for some strange reason, windows is being affected (yes, it supposedly fixed itself, then this morning, it stopped working and it's back in the same situation as ubuntu) 
 
hmm, thanks, that gives me some ideas, I'll try a few things
 
and yeah, it being BIOS related makes sense. around the same time the problem started happening, my BIOS gave me an error message that read "could not overclock" and asked me to either set some new settings on my BIOS or reset it to default settings. I have not overclocked and I checked to make sure a modifying software on windows didn't do it for me. Now I know things can sometimes display an incorrect error message while there is still an error, I'll go check that out
 
also, I'll see if I can get to the internet using ASUS Splashtop
 
honestly, if it were just wake on lan it wouldn't be affecting windows. windows keeps on saying that it's a broken lan cable when I've switched out the cables (I have a few extra lying around) and it still doesn't work and I can't explain why it worked for 2 boot ups and went back to not working again
 
also, since this is an edit, I tried ASUS express gate, and that doesn't work either, so I don't have the slightest clue what's going on, I'm almost tempted to make backups and completely reload all of my operating systems but I have a feeling that won't work

---

### Post by razor180 on 2010-07-30
alright, I just reset the BIOS to default settings and I'm still having the same problem

---

### Post by razor180 on 2010-07-31
I called my ISP, changed the driver, changed lan cables
 
I also figured out that my router isn't even detecting my computer (it will usually flash the number of the port a computer is directly connected to, but it's not doing that)
 
I reloaded the driver, I even flashed different BIOS versions, still not a difference
 
I have no idea what the problem is anymore

---

### Post by dineshs on 2010-07-31
Can you post the results of
```
sudo lshw -C network
```and
```
route -n
```

---

### Post by razor180 on 2010-08-01
sorry I haven't gotten around to testing those commands yet
 
but I did figure out that when I plug my computer directly into the modem that all of my operating systems except ubuntu works (which is probably just because of the realtek port) so, I don't know how or if the installation of openSUSE somehow screwed up my computer's connection to the router,
 
anyways, I'll probably ask that on a different forum, let's try to get ubuntu working

---

