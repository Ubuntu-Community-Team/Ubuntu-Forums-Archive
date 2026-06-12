---
title: "Version 10.04, no ethernet. Compaq CQ2025 Desktop"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by steveontario on 2012-02-05
Hi everybody,

Just got the above Compaq desktop (Compaq CQ2025), put v 10.04 alongside Windows, and can't get it to recognize the ethernet connection. Ethernet works, because I plugged the exact same cable into a netbook and it loaded web pages.

After some research, I found a number of threads in this and other forums explaining how to fix the issue. Most appear to be talking about loading some Intel ethernet controller, after discovering that lspci -v doesn't recognize a controller.

That's not the case with me -- lspci -v shows an HP ethernet controller.

Mind you, I have no idea how to interpret lspci output -- I don't understand the code side of Linux at all.

Anybody have any ideas how I can fix this?

---

### Post by aasdfasdfg on 2012-02-05
That's great that you have taken a look at the ```
lspci
``` output. It might be more helpful if you also ran ```
lshw -C network*
``` and posted the output this time. Furthermore, it might be helpful to post the contents of ```
/etc/network/interface
```. Lastly, what do you see when you run ```
ifconfig
```, and can you verify that the NetworkManager daemon is running?

---

### Post by varunendra on 2012-02-06
> **aasdfasdfg said:**
> ```
lshw -C network*
```
There should be no '*****' after '*network*' in the command, and it is recommended to run '*lshw'* with 'sudo'. Hence the correct use of the command would be:
```
sudo lshw -C network
```Also, the *lspci *command would give a long list of hardware, while we are interested only in the 'network' interfaces. Therefore a better form of the command to get only (and all) the relevant info is:
```
lspci -nnk | grep -iA2 [COLOR=Red]**net**[/COLOR]
```

---

### Post by mörgæs on 2012-02-06
Moved to the network forum.

---

### Post by steveontario on 2012-02-06
thanks everybody.

aasdfasdfg, you first. Here's the code you asked for.

lshw -C network *:
```
Hardware Lister (lshw) - B.02.14 
usage: lshw [-format] [-options ...] 
       lshw -version 

	-version        print program version (B.02.14) 

format can be 
	-html           output hardware tree as HTML 
	-xml            output hardware tree as XML 
	-short          output hardware paths 
	-businfo        output bus information 

options can be 
	-class CLASS    only show a certain class of hardware 
	-C CLASS        same as '-class CLASS' 
	-c CLASS        same as '-class CLASS' 
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
	-quiet          don't display status 
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 
	-numeric        output numeric IDs (for PCI, USB, etc.) 
```

/etc/network/interface:
```
No such file or directory 
```

ifconfig:
```
No command 'Ifconfig' found, did you mean: 
 Command 'fconfig' from package 'redboot-tools' (main) 
 Command 'ifconfig' from phackage 'net-tools' (main) 
Ifconfig: command not found 
```


varunendra, here's the code you requested.

lshw -C network	 (no “*” and I forgot to do it as a super-user, hence the warning):
```
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: AR8152 v2.0 Fast Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       version: c1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
       resources: memory:fea00000-fea3ffff ioport:e000(size=128)
```

lspci -nnk | grep -iA2:
```
Usage: grep [OPTION]... PATTERN [FILE]... 
Try `grep --help' for more information.
```

Hope this sheds some light.

Thanks for looking into this!

---

### Post by aasdfasdfg on 2012-02-06
As pointed out, I had some typos in the commands I posted but other users corrected; sorry about that.

Right now, the fact that ifconfig is not installed jumps out at me. You did a full Ubuntu install? Can you also verify that you have NetworkManager installed? Just run ```
NetworkManager
``` from a command line; if it gives a warning, it is installed.

I know it is annoying installing packages on a system without internet, but to move further you will most likely want to install ifconfig from the net-tools package and other dependencies it brings it. The only way I'm familiar with installing packages without internet is to use the graphical Synaptic package manager to generate an install script. See [here]("https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection").

---

### Post by varunendra on 2012-02-06
Ouch!! Looks like there is really "something" in your problem since we all are making a lot of typos (including you) ;)
> **steveontario said:**
> ```
/etc/network/interface
``` It should have been
```
cat /etc/network/interface[COLOR=Red]**s**[/COLOR]
```> **steveontario said:**
> 
```
No command 'Ifconfig' found,....
```
it should be all 'smalls' while you typed **I**fconfig ('i' in 'caps')

> **steveontario said:**
> lspci -nnk | grep -iA2:My mistake this time! :redface: I forgot the "net" in the last. Corrected in the original post.

Anyway, the useful info is here (and we don't need others till the correct driver is installed):
> **steveontario said:**
> 
lshw -C network     (no &#8220;*&#8221; and I forgot to do it as a super-user, hence the warning):
```
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: **AR8152 v2.0 Fast Ethernet **
       vendor: Atheros Communications
```

As a starting point (hope it also turns into 'ending point'), please try what is suggested in this post: [http://ubuntuforums.org/showpost.php?p=9446984&postcount=6](http://ubuntuforums.org/showpost.php?p=9446984&postcount=6)

I hope there are no critical typos this time!! :D

**_PS_:**
> **aasdfasdfg said:**
> Right now, the fact that ifconfig is not installed jumps out at me.
As pointed out above, now you know why it gave error ;)

---

### Post by steveontario on 2012-02-06
... and I should add that it's not just ethernet that's missing. There are no wireless networks indicated under that little network icon that's to the left of the date on the top-right of the screen.

---

### Post by chili555 on 2012-02-06
> It should have been
Code:

cat /etc/network/interface

In fact, it should be:```

cat /etc/network/interface**[COLOR="Red"]s[/COLOR]**


```You might also have better luck with:```
lspci -nn | grep -e 0200 -e 0280
```

---

### Post by varunendra on 2012-02-06
> **chili555 said:**
> In fact, it should be:```

cat /etc/network/interface**[COLOR=Red]s[/COLOR]**
```
:neutral: After all those corrections !!
:lolflag:

Thanks for the pointer (..and the rescue attempt :P). Correction no #3 in the original post on its way..

---

