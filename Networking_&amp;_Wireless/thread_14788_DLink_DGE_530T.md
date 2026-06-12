---
title: "DLink DGE 530T"
date: 2005-02-09
forum: Networking &amp; Wireless
---

### Post by BoBoB on 2005-02-09
Does anyone know how I get this adapter to work?
DLink has a linux driver for it, but I'm unable to compile it in Ubuntu.

I got it to work on a Slackware server with the 2.6.7 kernel, but the compiled file won't load on my Ubuntu server.

---

### Post by deangl on 2007-01-13
> **BoBoB said:**
> Does anyone know how I get this adapter to work?
DLink has a linux driver for it, but I'm unable to compile it in Ubuntu.

I got it to work on a Slackware server with the 2.6.7 kernel, but the compiled file won't load on my Ubuntu server.

Does anybody have this working on Dapper ???  Please reply to me ASAP - critcal project underway and time is of the essence.

---

### Post by Vilair on 2007-08-14
I am trying to install the drivers for my two DLink DGE 530T ethernet cards. I have the cd and am woundering how to install the drivers through command line only since my version dosn't have a X already installed. Any help would be appreciated. Thanks

---

### Post by danielmncastro on 2007-12-07
Simple algorithm: 

1) Get the driver from the CD

2) Get the necessary packages (apt-get or synaptic) to compile the driver: build-essentials and linux-headers

3) Create a symbolic link to the headers.
```
 # ln -s /usr/src/linux-headers /usr/src/linux
```

4) Change the symbolic link of the default shell from **dash** to **bash**
```
#rm /bin/sh
#ln -s /bin/bash /bin/sh
```

**OR**
Edit the **install.sh** script (that comes with the driver), changing the first line from 
```
#!/bin/sh
```
to
```
#!/bin/bash
```

5) Execute the **install.sh**. It will compile and install the driver.

6) Configure IP address and start using your new card.

- Daniel


[COLOR="Red"]**NOTE: The driver from D-Link website is outdated. DO NOT USE IT. Get the driver from the CD.**[/COLOR]

---

### Post by Return Privacy on 2008-06-02
Daniel,
I am trying to install this DLink DGE-530T gigabit card in Ubuntu 7.10 also. You wrote 

2) Get the necessary packages (apt-get or synaptic) to compile the driver: build-essentials and linux-headers

What does that mean? "compile", "linux-headers" etc?

I do have a "synaptic manager" showing in administration drop down at the top of the window?

I don't know any command line things. I just need to get the driver installed to make this card work in Ubuntu 7.10
I have the file "dge530t_driver_linux_610.tar" . I put this in a folder on the desktop. That is as far as I can go. I have no idea how to get this driver from this .tar file into wherever it goes?

This card isn't showing up at all in the "hardware" tab under administration?
Any help will be greatly appreciated!

---

### Post by TheRequiem13 on 2008-07-03
> **danielmncastro said:**
> Simple algorithm: 

1) Get the driver from the CD

2) Get the necessary packages (apt-get or synaptic) to compile the driver: build-essentials and linux-headers

3) Create a symbolic link to the headers.
```
 # ln -s /usr/src/linux-headers /usr/src/linux
```

4) Change the symbolic link of the default shell from **dash** to **bash**
```
#rm /bin/sh
#ln -s /bin/bash /bin/sh
```

**OR**
Edit the **install.sh** script (that comes with the driver), changing the first line from 
```
#!/bin/sh
```
to
```
#!/bin/bash
```

5) Execute the **install.sh**. It will compile and install the driver.

6) Configure IP address and start using your new card.

- Daniel


[COLOR="Red"]**NOTE: The driver from D-Link website is outdated. DO NOT USE IT. Get the driver from the CD.**[/COLOR]

Daniel,

I have tried following the steps you give, and come very close to success, with one small hitch.

When I do ```
apt-get install linux-headers
``` I am told to be more specific, and pick a version such as ```
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
```
and many more options.

Which should I install and link to? I have tried to use the two I gave as examples above, but the DLink install script fails due to unrecognize linux-headers, and does not complete the install.

I'm very close, but this is a brick wall for me.

Brendan

edit: ok, so I tried using ```
sudo apt-get install linux-headers-$(uname -r)
``` (which i found at [https://answers.launchpad.net/ubuntu/+question/9235](https://answers.launchpad.net/ubuntu/+question/9235) )and it grabbed version 2.6.24-19-server. I linked that to /usr/src/linux, and the install script **still failed**. It's last few lines of output are:

```
Execute: make oldconfig (done)                                       [   OK   ]
Check kernel header version (not recognized)                         [  warn  ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of sk98lin driver module failed.
```

Full log file: [http://www.goorpy.com/tmp/install.log](http://www.goorpy.com/tmp/install.log)

Now that I think I've got the right version being used, I'm at a complete loss as to why the script is failing.

Anybody have any suggestions?

---

### Post by Return Privacy on 2008-07-03
Hi all,
I saw the help you guys posted, but frankly it is WAY over my head. I asked the "linux" guy at the local computer repair shop and he said to just use an intel net card and it will work fine without having to compile or do anything. I took out the DLink, (which wasn't recognized) and put in the intel net card, and it works great! 
I would love to know how to do the "compile" thing to make a driver work, but it does seem complicated? Isn't there an easier way to put in a specific driver for a piece of hardware? Is there a good "beginners" tutorial to explain what "compile" means and how to do it in general?
Thanks for all the help, it is greatly appreciated!

---

