---
title: "Installing and Configuring TOR in Ubuntu 10.10 Maverick Meerkat"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by soresger on 2010-09-16
How can I install TOR (anonymity network) application and configure it to work correctly, as intended to do so?

I installed Vidalia using the 'Ubuntu Software Centre' but because I could not install the actual packages for the TOR program, I could not locate 'tor' in usr/bin while configuring Vidalia.

I tried to follow the instructions on Tor's official website but I still was not able to install the packages. I followed all of the instructions.

> You'll need to set up our package repository before you can fetch Tor. 

First, you need to figure out the name of your distribution. If you're using Ubuntu 10.04 it's "lucid", 9.10 is "karmic", 9.04 is "jaunty", 8.10 is "intrepid", and 8.04 is "hardy". 

If you're using Debian Etch, it's "etch", and Debian Lenny is "lenny". Then add this line to your /etc/apt/sources.list file:
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main

where you put the codename of your distribution (i.e. etch, lenny, sid, lucid, karmic, jaunty, intrepid, hardy or whatever it is) in place of <DISTRIBUTION>.

Then add the gpg key used to sign the packages by running the following commands at your command prompt:

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

Now refresh your sources and install Tor by running the following commands (as root) at your command prompt:

apt-get update

After following all of the above instructions I ran the last one, it was:

> sudo apt-get install tor tor-geoipdb

[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en) (here are the instructions)

Here is the error I got:

> owner@ubuntu:~$ sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'tor' has no installation candidate
E: Unable to locate package tor-geoipdb
owner@ubuntu:~$ 


I even gave myself administrator privileges but I still could not get it to work and I did use the sudo command too.

---

### Post by mkvnmtr on 2010-09-16
You may have made a typing error in the terminal. Try using software sources and synaptic,

---

### Post by CharlesA on 2010-09-16
Moved to Maverick area.

---

### Post by soresger on 2010-09-16
Synaptic Package Manager is not loading the new packages properly.

Error:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

> Failed to fetch [http://deb.torproject.org/torproject.org/dists/maverick/meerkat/binary-i386/Packages.gz](http://deb.torproject.org/torproject.org/dists/maverick/meerkat/binary-i386/Packages.gz)  404  Not Found [IP: 86.59.30.36 80]
Failed to fetch [http://deb.torproject.org/torproject.org/dists/maverick/main/binary-i386/Packages.gz](http://deb.torproject.org/torproject.org/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 86.59.30.36 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by dino99 on 2010-09-16
as i know this package is available for lucid, so update your synaptic sources tab

---

### Post by soresger on 2010-09-16
> **dino99 said:**
> as i know this package is available for lucid, so update your synaptic sources tab

I renamed the <DISTRIBUTION> part with lucid it installed all good but I can not configure it to work properly.

Here is the error log:

> Sep 16 16:09:13.848 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 16 16:09:13.848 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 16 16:09:13.848 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 16 16:09:13.848 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 16 16:09:13.848 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 16 16:09:13.849 [Error] Reading config failed--see warnings above.

I browsed to the TORRC file and opened it with a text editor and found out that it was completely empty! Not a single line of code.

What shall I do?

---

### Post by soresger on 2010-09-16
Okay. So I stopped tor through bash by typing 

> sudo /etc/init.d/tor stop

Then I relaunced Vidilia and it connected to the TOR network successfully on Firefox when I also got the TorButton addon installed. Now the only issue is 'how can I configure TOR to work with the Chromium browser?'

---

### Post by dino99 on 2010-09-16
maybe use google or anything you like to find a howto

---

### Post by soresger on 2010-09-16
> **soresger said:**
> Okay. So I stopped tor through bash by typing 



Then I relaunced Vidilia and it connected to the TOR network successfully on Firefox when I also got the TorButton addon installed. Now the only issue is 'how can I configure TOR to work with the Chromium browser?'

Again. I launched the Chromium browser, went to options and into proxy settings, typed 127.0.0.1 for the address and 8118 for the port and it worked. Only thing is, I have to always manually select/deselect the proxy settings in the Chromium browser when I want to enable or disable Tor for Chromium. I now need to check some tutorials on how to torify an application.

---

### Post by SevenMachines on 2010-09-16
Just a quick note, to disable tor, so it doesnt start on boot (so vidalia can start it), edit file below and set run daemon to no.

/etc/default/tor:
> 
RUN_DAEMON="no"
As for chromium proxy switchers..
[https://chrome.google.com/extensions/search?itemlang=&q=proxy+switch](https://chrome.google.com/extensions/search?itemlang=&q=proxy+switch)

I dont use it though so someone else will probably now some better ones

---

### Post by soresger on 2010-09-16
@SevenMachines thank you for the tip.

I copied the original 'tor' file onto my desktop to grant it permission so that it can be edited and saved. Then I browsed to the directory removed the original tor from the /etc/default directory using the following command:

> sudo rm tor

Then I browsed to and restored the file I had saved onto my desktop into the /etc/default directory by using the following command:

> sudo mv tor /etc/default

---

### Post by SevenMachines on 2010-09-16
Well the move wasnt strictly neccessary, something like
> $ sudo gedit /etc/default/tor
would have worked too. Either way, its set up for properly for vidalia use though, which is good :)

---

### Post by soresger on 2010-09-16
> **SevenMachines said:**
> Well the move wasnt strictly neccessary, something like

would have worked too. Either way, its set up for properly for vidalia use though, which is good :)

oh great thanks
well im new to the linux shellcode :D

---

