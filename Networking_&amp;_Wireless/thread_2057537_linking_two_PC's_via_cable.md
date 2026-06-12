---
title: "linking two PC's via cable"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by timbo59 on 2012-09-13
I have a real problem I'm trying to figure out.

I had an external drive that I used to back up all my data from my Ubuntu-based PC, and the storage unit died on me recently. As is usual with these things, it was the controller that burnt out, not the drive itself. I cracked open the case, took out the HD, and slotted it into the only PC I have with the capacity to accommodate extra drives, my Windows-based PC - the HD works fine. Unfortunately, some of the data files, including some music files, come up as errors via Windows, yet I know they're perfectly fine under Ubuntu - it has something to do with the naming, and even though I've tried to change them to accommodate Windows it won't let me - it just lists them as new types of errors. 

I had actually done a clean install on my Ubuntu PC with the latest update, and was transferring data back on the PC when all this happened - it just has to happen like that, right? But here's the problem - I thought I could get around the issue by simply transferring the data to the Ubuntu PC via flash drives, but when I try to transfer the data to the sticks, Windows will only transfer what Windows considers to be okay - the rest of the stuff it considers corrupt stays behind. Talk about a pain in the butt!

So, I went out and bought a USB to USB file share cable for $40 that will supposedly allow me to hook the two PC's directly up. My hope is that I can then access all the data on the Windows PC and transfer it across to the Ubuntu PC WITH all the stuff Windows won't recognize. Question, will there be a compatibility issue between the two operating systems recognizing each other for the transfer? And will Windows allow access to the files it considers corrupt or no longer on the drive? I haven't opened the cable packet yet as I didn't want to simply throw $40 away for nothing.

The only other way I can think of to get around this is to load Ubuntu side by side on the Windows PC to help the transfer across. Or Can I network the two OS systems together without having to hook them up directly?

Any thoughts?

---

### Post by jonobr on 2012-09-13
Hello


Not sure Im reading this correctly or if Im just tired ):P but here goes,

If the two machines are on the same network, why not install (if you havent already
openssh
open a terminal
```
sudo apt-get install openssh-server
```
 on the ubuntu server
and winscp on the windows.
With winscp installed,
fire it up, put in the IP address of the ubuntu machine,
enter username and password,

You should be able to drag and drop files to your home directory or vice versa

Again,
may not be understanding you fully

---

### Post by timbo59 on 2012-09-14
No, you're fine. Probably thinking could anyone be THIS dumb! Even though we have half a dozen PC's, laptops, iPads, Macs etc running off the house wireless router, I've never actually tried hooking any of them up together before. About all we use in common is the wireless printer.

So let me get this right. My Windows PC and the the Ubuntu PC are both linked directly to the back of the router, so all I have to do is type in the lines you suggested and both computers will recognize each other across different operating systems?

Sorry for sounding so dopey on the subject. Simply never had any need before to link computers before. On the odd occasion we need to transfer anything, I usually pull out a flash drive and use that. Or, if it's small enough, I just email it across.

It's a bit late for me right now (nearly 1:00am) but I'll give your suggestion a whirl in the morning.


Thanks.

---

### Post by jonobr on 2012-09-14
Understood,

No problem,


So with your ubuntu and windows connected,
the two applications give you the ability to copy across your network securely.

On Ubuntu opening a terminal window and running the 
```
sudo apt-get install openssh-server
```
installs a server that allows you to connect to it from other machines or to copy files to and from your ubuntu box.

The winscp program for windows once installed, allows you to connect to the openssh server.

Once both are installed you would use your existing username and password to login.
So you need those.

You will also need the IP address of the ubuntu box.
You can get that by typing

```
ifconfig
```
in a terminal window of the ubuntu box
The ip address will probably be 192.168.1.X or something like that.

Put that IP address in the winscp host field and  hit enter
it should ask for a username and password.
After a short while it should login and you should see your home directory.
You can then grab multiple files and copy.,

You can also use Openssh on ubuntu to login to you machine remotely in cli using a program on windows like putty.

This will use secure shell to login to your machine.

You can user fancier ways like using samba file shares, but I imagine all you want to do right now is mvoe your data

night

---

### Post by redmk2 on 2012-09-14
> **timbo59 said:**
> No, you're fine. Probably thinking could anyone be THIS dumb! Even though we have half a dozen PC's, laptops, iPads, Macs etc running off the house wireless router, I've never actually tried hooking any of them up together before. About all we use in common is the wireless printer.

So let me get this right. My Windows PC and the the Ubuntu PC are both linked directly to the back of the router, so all I have to do is type in the lines you suggested and both computers will recognize each other across different operating systems?

Sorry for sounding so dopey on the subject. Simply never had any need before to link computers before. On the odd occasion we need to transfer anything, I usually pull out a flash drive and use that. Or, if it's small enough, I just email it across.

It's a bit late for me right now (nearly 1:00am) but I'll give your suggestion a whirl in the morning.


Thanks.

Any machine that communicates via your house router (wired or wireless) can communicate with the other machines on the local network as long as they are in the same local network (LAN).  I would suspect they do.  To check you can always ping one machine from another.  You will either need to know the IP address of the machine you are pinging or its hostname.

If you can ping each other you have TCP/IP connectivity.  The application OpenSSH runs on any TCP/IP network and can be used by Linux (Ubuntu), Windows and Apple (IOS or OSX).

What @jonobr has suggested is correct.  SSH is the application protocol and the both OpenSSH and WinSCP understand it.  It doesn't matter whether it is on Ubuntu or Windows.

You want to install the SSH Server on Ubuntu and the SSH Client (WinSCP) on the Windows machines.  The Windows SSH client (WinSCP) can be found [**_[COLOR="Blue"]here[/COLOR]_**]("http://winscp.net/eng/download.php").

---

### Post by timbo59 on 2012-09-14
Well, I tried, but for all that effort I came up against the same problem. All the suggestions you made worked just fine, but as soon as I tried transferring the problem files across from the Windows PC they registered as errors. 

I just can't seem to work around the fact that files that worked just fine in a Linux environment won't function in ANY capacity in a Windows environment, even when trying to transfer across to an Ubuntu-based system. In essence, I've tried turning my Windows-based PC into one over-sized external HD for the drive that came out of the unit that broke down on me, but because Windows is on board it's getting in the way. In many cases Windows just registers an error message that the files are no longer present, yet I know for certain that they are. I did an experiment by placing similar files from my Ubuntu PC on to a flash drive, and if I connect the stick to my Windows PC they again come up as no-longer-in-existence errors. 

The only two things I can think of are to try and set up Ubuntu side by side with Windows 7 on the same machine and see if that will allow me to make the transfer, or go to the expense of buying another external hard drive, crack it open, and replace the HD inside it with the one from the unit that broke down on me. Then I can hook it up directly to the Ubuntu PC. 

What a pain!

---

### Post by mevun on 2012-09-14
Have you looked into some sort of data duplicator utility?  Maybe there is something on the Windows side that can extract files from so-called unknown formats.  The problem is that it might not really work doing that, because of how the disk information has to also be properly "copied" to a new destination.

> **timbo59 said:**
> 

The only two things I can think of are to try and set up Ubuntu side by side with Windows 7 on the same machine and see if that will allow me to make the transfer, or go to the expense of buying another external hard drive, crack it open, and replace the HD inside it with the one from the unit that broke down on me. Then I can hook it up directly to the Ubuntu PC. 

What a pain!

Note: If you are going to buy another external hard drive, you should know that you can also just buy an external enclosure which will take a typical harddrive.  They come in 2.5 and 3.5 inch sizes, but all new ones probably only accept SATA drives.  If you buy an external harddrive (basically an enclosure with a harddrive already), then you'll probably void its warranty by opening it.  Of course, you might think this is a better use of your money even if it costs more than just an enclosure.

---

### Post by oldfred on 2012-09-14
I think mevun's suggestion of a separate USB enclosure is a choice.

You should be able to use a liveCD or USB and boot with that on your Windows system. Then you could rename or copy files to a USB or use the SSH to copy the files.

If you have a network of computers you do need to learn about SSH, Samba and/or NFS. Then all the computers can talk to each other.

 I used Samba for a while, many suggested I use SSH as I only occasionally sync'd my two computers. But I jsut gave up on XP and installed Ubuntu on my laptop, so I could use NFS to sync them. Samba will work to let Windows machines talk to Linux.

When you mount a NTFS partition add windows_names to mount parameters.

For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by timbo59 on 2012-09-14
Actually, I tried that approach this morning by shopping around at places like CompUSA to see if I could simply by a case to slip the HD into, but they didn't have any and I began to wonder if anyone actually made/sold them. It would obviously be the easy fix to my problem.

Here's another thought. When I ran into problems this morning trying to transfer the data, I was trying to perform the action from the Windows PC via WinSCP. I thought I might have more luck trying to make the transfer from the Ubuntu PC, but I can't for the life of me see where/how to access SSH on the Ubuntu PC to try and link over to the Windows PC. What am I missing?

---

### Post by mevun on 2012-09-14
> **timbo59 said:**
> Actually, I tried that approach this morning by shopping around at places like CompUSA to see if I could simply by a case to slip the HD into, but they didn't have any and I began to wonder if anyone actually made/sold them. It would obviously be the easy fix to my problem.


I don't think you'll find the enclosure in a run-of-the-mill brick-and-mortar computer store (although I thought CompUSA would have them).  BestBuy certainly won't.  I think MicroCenter will (if you have one nearby), but check their website to be sure.  So if you don't want to do mail order, then you might be stuck with the external HD.

> 
Here's another thought. When I ran into problems this morning trying to transfer the data, I was trying to perform the action from the Windows PC via WinSCP. I thought I might have more luck trying to make the transfer from the Ubuntu PC, but I can't for the life of me see where/how to access SSH on the Ubuntu PC to try and link over to the Windows PC. What am I missing?Maybe try this:
[http://askubuntu.com/questions/112014/nautilus-sftp-via-command-line](http://askubuntu.com/questions/112014/nautilus-sftp-via-command-line)

---

### Post by jonobr on 2012-09-14
> Here's another thought. When I ran into problems this morning trying to transfer the data, I was trying to perform the action from the Windows PC via WinSCP. I thought I might have more luck trying to make the transfer from the Ubuntu PC, but I can't for the life of me see where/how to access SSH on the Ubuntu PC to try and link over to the Windows PC. What am I missing?

Hi there

In the setup you now have, ubuntu is the server and the windows pc is the client.

What your trying to do is use the ubuntu servers client ssh program to connect to the windows machine but it does not have an ssh server running on it.

What you could do is install an ftp server on your windows machine
FTP is old and insecure but good for quick painless setup and transfer.

You could setup filezilla server on your windows machine.
When you set it up,
Add a group with all permissions (read write upload etc)
then under the shared folders tab, click add.
Browse to the location of your stuff.
When you have that addess lick ok.

Then go into the user tab,.
Add a users , add him to the group you just created.

Then start the filezilla server. Then.... sigh.... go over to the ubuntu machine open a terminal and type

```
ftp <ipaddress of windows box>
should say connected
user <enter username>
password <enter password>
```

check you in the correct folder and can see your file (type dir or ls)

then type the following commands
```

bin
hash
prompt
mget *
```
All the files (partial and full) should start to copy over.
When finished
type
```
bye
```

When back in the terminal on ubuntu type ls
you should see all the files

---

### Post by timbo59 on 2012-09-14
Okay, I got it sorted out, thanks to asuggestion from another thread. It never occurred to me that you could use the install disk for Ubuntu simply to trial the OS, which is what was suggested. Sure enough, as soon as I booted up from it and instructed Ubuntu that I merely wanted to take a test run, it allowed me access to the file areas I needed. I shifted 1 gig's worth on to a flash drive just to see how things went, and presto, it worked! All the files, including the ones Windows kept saying were either trash or no longer available, went on the stick, and I double checked by plugging it into the Ubuntu PC. All was A-okay. 

So there you go! No need for new external HD's - at least to solve this particular problem - no need to monkey around with the hardware, and no need to try and make the two PC's cooperate in the venture. Though I do appreciate some of the points I picked up, not least in how to network the PC's. That will come in handy.

Thanks to all for their input - very much appreciated.

---

