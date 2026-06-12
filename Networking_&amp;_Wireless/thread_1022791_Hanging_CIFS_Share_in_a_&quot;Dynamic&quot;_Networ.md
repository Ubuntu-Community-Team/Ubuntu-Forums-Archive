---
title: "Hanging CIFS Share in a &quot;Dynamic&quot; Network Config"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by ytene on 2008-12-27
Hey everyone... I've been having some fun with my Hardy “Development” server and it's network setup, and after some tinkering with a new problem, I got to an interim solution that falls short of my ideal state. But I've learned a few bits and pieces and thought I'd share in the hope that what follows is either useful, or, even better, that someone may be able to help answer my last 2 questions... So here goes.

Preamble
I have a PC on which I run various OS images by means of SATA caddy units. One such image consists of Ubuntu 8.04 configured to be a development server – so in addition to typical desktop tools, it has BIND, Apache, MySQL, PHP and a few other goodies on it. Having got this up and running, my idea was to write a simple script that would “flip” between this “local” setup and an internet-facing variant. The internet variant would need to shut down Apache, MySQL and Bind and so on.

I wrote a simple script, netswap, that allows me to do this. Here is a copy of that script:-

#=========================================================
# Notes
# In order to use this script, a total of four files must first
# be created, containing the corresponding information for both
# the "internet" and "local" network connections, for bind9 and
# the network.
#
# The convention used in this script is to have these four 
# "primer" files configured with the following [full] path 
# names: -
#
#  /etc/resolv.conf_local
#  /etc/resolv.conf_internet
#
#  /etc/network/interfaces_local
#  /etc/network/interfaces_internet
#
# Create the above named files [or their equivalents if your
# distro is structured differently] and then place this script
# in your shell path. You must be root to use this script.

# Test for root
if [ "$(id -u)" != "0" ]; then
	echo "This script is only available to the root user."
	exit 1
fi

case "${1:-''}" in
  'local')
	if [ ! -f /etc/network/interfaces_local ]; then
		echo "Cannot find /etc/network/interfaces_local."
		exit 1
	fi
	if [ ! -f /etc/resolv.conf_local ]; then
		echo "Cannot find /etc/resolv.conf_local."
		exit 1
	fi
	cp /etc/network/interfaces_local /etc/network/interfaces
	cp /etc/resolv.conf_local /etc/resolv.conf
	/etc/init.d/apache2 start
	/etc/init.d/mysql start
	/etc/init.d/networking restart
	/etc/init.d/bind9 start 
	echo "Successfully converted to Local Network Config..."
	;;

  'net')
	if [ ! -f /etc/network/interfaces_internet ]; then
		echo "Cannot find /etc/network/interfaces_internet."
		exit 1
	fi
	if [ ! -f /etc/resolv.conf_internet ]; then
		echo "Cannot find /etc/resolv.conf_internet."
		exit 1
	fi
	echo "About to copy interfaces_internet to interfaces."
	cp /etc/network/interfaces_internet /etc/network/interfaces
	cp /etc/resolv.conf_internet /etc/resolv.conf
	/etc/init.d/apache2 stop
	/etc/init.d/mysql stop
	/etc/init.d/bind9 stop
	/etc/init.d/networking restart
	echo "Successfully converted to Internet Network Config..."
	;;

  'status')
	ifconfig -a
  	;;

  *)
	echo "Usage: $SELF local|net|status"
	exit 1
	;;
esac
#=========================================================

As you can see, it's not clever [ !! ] but it works just fine.

Just recently, I purchased an Apple Time Capsule [ which acts as additional storage for my Mac Mini ]. I can mount the capsule from my ubuntu machine by adding the following line to my fstab file :-

//192.168.1.39/TimeCapsule/clive /media/capsule cifs password={password},rw,iocharset=utf8,file_mode=0777,dir_mode=0777

where {password} is in fact specified during the setup of the Time Capsule itself and hard-coded into my fstab entry. Unfortunately, this is where the problems struck. The moment I added the above statement to my fstab file, my “netswap” script stopped working. I had already augmented my “local” copy of the interfaces file to include routing to the 192.168.1.* network, and when switching from “internet” facing to “local” facing, everything seemed to work fine. Flipping back the other way, however, caused my netswap script to hang when it reached the statement,

/etc/init.d/networking restart

I did a little bit more digging [ the above script is shown in debugging form; when clean I append “&2>/dev/null” to the execute statements to mask chatter. Eventually, I got an error message that hinted the problem was due to the fact that the networking stack was unable to cleanly disconnect from the Time Capsule. I referenced the man pages and the CIFS documentation and tried augmenting my script with

umount -f /media/capsule

which unfortunately has made no difference whatsoever. I have observed that when I experiment with the netswap script and try to move between local and internet state, use of “df -k” between swaps can show that I have multiple mounted connections to the Time Capsule – so they are being set up but are not closing down cleanly. 

Wow – sorry for the long explanation. 

So the tip is – if you're using a Time Capsule then the above statement will give you read/write access from an ubuntu machine. [sorry, this might apply to other SAMBA/CIFS Shares, but I can't validate that with this configuration]. 

Here are my questions:-

1.Would anybody be able to help me resolve this issue with a clean and permanent way to cut a CIFS connection that could be inserted into the above "netswap" script please?

2.Failing that, the next option [ and it's a dirty kludge ] would be for me to replicate my Audio file data between the Time Capsule and my ubuntu machine on an ad-hoc basis. I'm thinking that something like rsync might be able to do this for me, but there are many options to choose from and I'd appreciate guidance on where to start. On both the Capsule and the ubuntu machine I'm going to have a data directory structure set up such that I might want to perform a 2-way synchronisation of either all or part of the structure. So...

	dirsync tunes		- would just synchronise the music library

	dirsync office		- would just synchronise my documents

or

	dirsync all		- would go to the top of the data tree and do the lot

Would anybody care to suggest a suitable approach, perhaps pointing me at some novice-level how-to guides please? 

Thanks in advance!

---

### Post by mpokrywka on 2008-12-27
> **ytene said:**
> 
1.Would anybody be able to help me resolve this issue with a clean and permanent way to cut a CIFS connection that could be inserted into the above "netswap" script please?


I think you should disable/stop any programs that use that "time capsule".
If you don't know who is responsible, try:
**lsof /media/capsule**
and that should tell you what is responsible for keeping cifs connection open.
So script should:
stop all programs accessing /media/capsule
umount /media/capsule
then reconfigure network

---

### Post by ytene on 2008-12-28
Thanks for that clue - I will give that a try.

Since making the original post I have continued my experimentation and made a couple of further refinements. Firstly, I have modified my /etc/fstab file, so the string which used to read this:-

//192.168.1.39/TimeCapsule/clive /media/capsule cifs password={password},rw,iocharset=utf8,file_mode=07 77,dir_mode=0777

now looks like this:-

//192.168.1.39/TimeCapsule/clive /media/capsule cifs password={password},rw,iocharset=utf8

Although I seem to get the same functionality, the connection does not write files to the Capsule with 'root' ownership or permissions. It took me a little while to get to this. I had been experimenting with unison as a directory synchronization tool and even though it seemed to work reasonably well, the interactive session gave errors about it being unable to set file permissions. The trail of evidence led me to the above change as an experiment and all seems ok so far.

I've just experimented with the lsof utility and it does seem to identify files traversing that link, so will have a deeper go and will report back. Thanks for the tip!

---

