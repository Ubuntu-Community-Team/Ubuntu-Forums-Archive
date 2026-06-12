---
title: "Atheros 9285 issues"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Ernie S. on 2010-04-05
Let me begin by saying that I am a total noob. I have probably over explained alot here, but I felt that being a windows zombie myself, others out there
may appreciate a little more in depth troubleshooting info. The terminal has a steep learning curve for those of us who have been using windows since 3.1. I
used dos and dosshell for a while, but I have forgotten everything I knew as a kid (not that any of it is applicable here anyway) So, here is my story.

  I had the worst time getting wireless working within ubuntu. This is a chronicle (from memory so it may not be totally accurate) of my journey.
It began with my Wibu install of 9.04. The wireless did no work "out of the box" so I started reading online. Turns out I wasn't the only one with a problem,
hence this post. My system is a Gateway LT3103u netbook with an Atheros 9285 wifi card. Apparently this card has a very bloody history with Linux. 
The first recommendation I tried was "sudo apt-get install Linux-backports-modules-jaunty" which worked at first, then caused my system to freeze.
And I mean FREEZE to the point I had to pull the battery in order to reboot. Next I decided to upgrade to 9.10 as some people said it should work 
out of the box. It worked, but was extremely unstable. It would disconnect at random times and require re-authentication. At this point I decided to try
a legacy solution and installed ndiswrapper. This made the problem even worse. My wifi started disconnecting every 30 seconds or so and finally degraded
to the point where my wifi card was not even recognized anymore. Now I was back to square 1. Using a wired connection I was browsing the online forums at 
help.ubuntu.com while downloading the beta 2 release of 10.04 hopeing this would work out of the box. Something caught my eye where someone had mentioned 
blacklisting the ath5k driver. I realized this was not the same chipset as my wifi card (which uses ath9k), but I decided to have a look. I cancelled the 
download of the beta 2 upgrade and used the GUI to navigate to /etc/modprobe.d. There I saw a file called blacklist-ath_pci.conf. I opened the file in the
text editor and saw it had one line: blacklist ath_pci. So I placed a # in front of the command, so it looked like this: # blacklist ath_pci. I then saved
it to my home folder. Realizing I would need to be root to save this to the modprobe.d directory, I entered the terminal and used the following commands: 


sudo cp /etc/modprobe.d/blacklist-ath_pci Desktop
                This was to create a backup of the original file

sudo mv blacklist-ath_pci.conf /etc/modprobe.d
                This was to move the saved file in the home dir to the modprobe.d dir

Then to confirm the operation worked I typed:

cd /etc/modprobe.d
cat blacklist-ath_pci.conf

This was the result.

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
# blacklist ath_pci

I then rebooted into unbuntu. From this point on, my wifi was detected and I was able to connect. I was having problems with the machine not recognizing
the connection though. any time I tried to ping something outside of localhost I had no connectivity! The wifi widget showed it was connected, but I could
not use the connection at all. This was easily corrected though by going to System>Preferences>Network Connections and deleting the wifi profile. 
From there I created a new connection from the wifi widget (in the top left corner of the default ubuntu desktop). Since then it's been smooth sailing. 
I even uploaded this post using wifi! I hope this finally works. I love Linux and I really want to continue using it as my primary home system. 
Unfortunately my employer is still scared of open source software and so we are stuck with Vista at work. I posted this for those who feel they have tried "everything" and are
thinking they are stuck with Windows.

---

### Post by Iowan on 2010-04-06
Laptops and wireless seem to be tricky to set up. Glad you found (or created) the solutions to your setup problems.
> Unfortunately my employer is still scared of open source software and so we are stuck with Vista at work. The large corporation I work for still uses XP. I doubt they will go Ubuntu soon, but maybe they'll skip Vista.

---

### Post by akikumar on 2010-04-15
I have AR9285 card ! I just installed ubuntu with window 7....Here is my question before doing this

1. Do i need to install madfi before or its preinstalled with 9.04 Jaunty

2. I tried installing mas fi before got this error

```

make

/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath/if_ath_pci.c:203: error:  'struct net_device' has no member named 'owner' 
make[3]: *** [/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath/if_ath_pci.o]  Error 1 
make[2]: *** [/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath] Error 2 
make[1]: *** [_module_/home/akshay/Desktop/aKI/madwifi-0.9.3.2] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 

```

```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285  Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
  
```

---

### Post by Ernie S. on 2010-09-19
I realize this thread is dead, but it still gets a few views so for those that stumble across it, no you do not need to install madwifi with ubuntu. The latest ath9k driver works just fine with this card. As a last resort you can install ndiswrapper and use the windows drivers, but this method WILL NOT work with aircrack-ng. To get aircrack working after an ndiswrapper install you have to unload the ndiswrapper module and load ath9k.

```

sudo rmmod ndiswrapper
sudo modprobe ath9k

```

Cheers

---

