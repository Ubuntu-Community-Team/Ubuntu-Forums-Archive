---
title: "Another &quot;cant get wireless to work&quot;"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by loseby on 2011-06-15
Am using Linux 11 and the card is a D link PCI card DWA525 which uses the RaLink 3060 chipset . Downloaded the driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and that is where I am.

A complete newbie to wireless ( but did get the win7 wireless and mobile phone to work through the Billion wireless router ) and pretty much a novice when it comes to anything linux.

How do you install the driver once you downloaded it and how do you check that the driver has installed correctly ? My guess would be to get that successfully installed and maybe probs solved.


btw: at my first attempt at installing wireless the driver showed as a RT 2800 pci which doesnt match the link above which shows the driver as an RT2860_Linux_STA_V2.4.00.tar.bz2 ( thats the name of the file I downloaded )

---

### Post by garvinrick4 on 2011-06-15
Put the tarbal where you want and extract it. Can just right click and open with archive manager if that is easier for you than command line. Now start by opening read me file and
it should tell you how to install. Usually just have to change directorys until where you get
to where tarball is extracted and run a few commands. It will install for you with the commands told to you in the read me file. If it is on the Desktop for instance. Usually
something like this or close to the read me file will tell you usually.
cd Desktop
ls
cd  to name of extracted directory 
make
make install

---

### Post by garvinrick4 on 2011-06-15
Here is a simple explanation:

Suppose you have a source file name src.tar.gz, what you do initially is that you need to extract the source files and then in the terminal&#8230;. 
navigate to the folder where the source file is extracted using the cd commands&#8230;.. and then 
type the following&#8230; 

./configure 

make 

sudo make install 

clean install 

lets see what each one of them does&#8230; 

./configure&#8230;.. checks whether the required dependencies are available on your system or not&#8230;.. if not an error is reported&#8230;. 

make...... compiles the source code and make install is used to install the program in to the location 

if it asks for an installation location it is recommended to install all the source to /usr/src 

clean install...... removes any temporary files created in the installation process of the source and thats it your source file in installed in your system.

---

### Post by garvinrick4 on 2011-06-15
Here is a link with instructions hope it helps you:

[http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html](http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html)

---

### Post by loseby on 2011-06-15
> **garvinrick4 said:**
> Put the tarbal where you want and extract it. Can just right click and open with archive manager if that is easier for you than command line. 

I did try that but I assumed I did something wrong as I received an error message. Actually tried quite a few things and thought I would go right back to the start .

> an error occurred while loading the archive

bzip2 - is not a bzip file
tar - child returned status 2
tar - error is not recoverable... exiting now



> **garvinrick4 said:**
> Here is a link with instructions hope it helps you:

[http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html](http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html)


well tried that but am unsure about the following
   > Now edit the following file
 vi  /etc/modeprob.d/blacklist.conf

Append the following line at the end of the file

    blacklist rt2800pci

I assume that this stops the driver that is already installed but how do you do this ? where is the location of this file and how to you edit ?

I just did another attempt and it shows the driver as the rt2800 pci and I assume we dont want this ( yes...still doesnt work )


Another edit :

found this file  blacklist-modem.conf in etc/modprobe.d  I assume the vi is another type of linux os and that is the file I need to add the blacklist but I cant save the file because I dont have permissions............so how do I get permissions ?

---

### Post by garvinrick4 on 2011-06-16
> so how do I get permissions ?     ```
gksudo gedit /now/path/to/file
```Above will open you up with powers just make changes and hit save.

 > I assume the vi is another type of linux os
vi is a text editor in terminal (with GUI can use gedit is simpler)

---

### Post by loseby on 2011-06-18
wireless now works


have the 3060 driver showing  and am using the wireless machine to send this


a big thanks for all the help

---

