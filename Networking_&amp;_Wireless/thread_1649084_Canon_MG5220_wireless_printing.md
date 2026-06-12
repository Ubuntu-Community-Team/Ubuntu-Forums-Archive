---
title: "Canon MG5220 wireless printing"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by lmanalo on 2010-12-19
Hi,

I just bought a new wireless printer. I have it set up on my wireless network and can use it with windows 7 just fine. When I try to set up a new printer in Ubuntu 10.10 it doesn't see it. I verified the IP address of the printer and typed it in the network printer setup utility but it keeps saying that it can't find a printer at that address.

Any help will be greatly appreciated. Also, I'm fairly new to Linux so please keep it simple.

THANKS!

---

### Post by walt.smith1960 on 2010-12-19
Here might be something to take a look at.  Page 3 in particular

[http://support-my.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&start=20](http://support-my.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&start=20)
[MG5200 series IJ Printer Driver Ver. 3.40 for Linux (debian **...**]("http://support-my.canon-asia.com/contents/MY/EN/0100301702.html")

I find it interesting that these are available on Canon's Asian site but not on their North American site.  Oh well.  If you haven't had experience with .deb packages, they're very much like Windows .exe files. You just need an installer, i.e. Ubuntu Software Center or Gdebi.  Apologies if you already know this.

---

### Post by walt.smith1960 on 2010-12-19
double post deleted

---

### Post by lmanalo on 2010-12-19
Thank you for the information. I looked at the driver - it's a tar.gz. I haven't had much experience working with tar.gz files. Time to do some more reading.
 
The problem I'm having is ubuntu isn't seeing that there is a printer on the network. I can ping it but when I go to the printer setup, type in the IP, and select find printer it says no printer found.

---

### Post by lmanalo on 2010-12-19
Ok, I downloaded the tar.gz and used the tar command to unpack it. There's no read me file to tell me what to do next. I have a series of .deb and lc files - what do I do with them?

thank you

---

### Post by lmanalo on 2010-12-19
I figured it out and it works great!

Thank you for the help.

---

### Post by walt.smith1960 on 2010-12-20
I'm glad it worked for you.  I don't know why Canon would put this on their Asian support site but not North America.  I've heard of other situations like this from other manufacturers. I guess the lesson is to expand our search for hardware support.

---

### Post by grege on 2010-12-20
The European Canon sites have 32bit drivers as well.

I have an MP640 and it works with printing and scanning over the network.

I recently went 64bit and had to manually force install the drivers, it was tedious but now works fine.

At least they provide drivers.

---

### Post by walt.smith1960 on 2010-12-21
> **grege said:**
> The European Canon sites have 32bit drivers as well.

I have an MP640 and it works with printing and scanning over the network.

I recently went 64bit and had to manually force install the drivers, it was tedious but now works fine.

At least they provide drivers.

Installing Brother's scanner driver on a 64 bit machine was the same - install from the command line using --force but as you say, at least they're available and they work.

---

### Post by epomerantz on 2011-01-06
Hello,

Thank you for helping to get this working for my linux box I have it installed and running but I have just one question to add on about this same printer. I want to know if and how I can get the scanner to send the pictures to the same linux machine? Is there a need to get any other software to make this happen? Thanks again for your help

---

### Post by mdwy62 on 2011-02-21
> **lmanalo said:**
> I figured it out and it works great!

Thank you for the help.

Glad this worked for you - could you publish what you did? When I unpacked 
cnijfilter-mg5200series-3.40-1-deb.tar.gz, I get a folder with a .deb extension, rather than an actual deb package. Within the folder is an install.sh file. If I type sudo ./install.sh, it complains that "The package management system cannot be identified." Under the packages subfolder there are to Intel (i386) and two AMD packages. Should I install the common one first and then the 5200 package for my processor (Intel)?

Thanks.

---

### Post by calast on 2011-03-05
I just tried this, downloading the deb packages from the Canon Asian web site. The scanner one installed fine, but the printer driver gave me an error when running the install.sh script:

install.sh: 588: Syntax error: Bad for loop variable

which would be:

                for (( i=0; i<$P_target_model_num; i++ ))

Well, I've been using Unix for 30 years and am OK with shell scripts, but this one is 1819 lines long - a bit much for me to debug. 

Has anyone else run into this? Is there some command line argument I was supposed provide?

---

### Post by stringkarma on 2011-06-18
@mdwy62, @calast: I didn't use the install.sh script. Go into the "packages" folder, for your architecture (32bit vs 64bit) install the common and then the specific packages, in that order. Worked for me.

---

