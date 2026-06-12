---
title: "Jaunty 9.04 Blind to XP's Shared Network Printer"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by celem on 2009-04-27
I am using Ubuntu Jaunty 9.10 e/w all current updates.

First let me state that the Windows Networked/Shared printer can be utilized just fine by two other Linux computers on mine - (1) a Dell 910 Netbook running Ubuntu 8.04 and another computer running Xubuntu 8.10. I print just fine from these machines, but NOT Jaunty 9.04.

There are a number of posts in GENERAL regarding Jaunty having various problems with Networked Printers, but none quite like my problem. I feel that this is actually a networking/SAMBA issue, so that is why I posted it here.

When I try to add a printer attached to and shared on my Windows XP box with System->Administration->Printing, New->Network Printer->Windows Printer via SAMBA, Browse - I get right up to where clicking the little gray diamonds should reveal a networked printer and Poof the dialog crashes and is gone.

*Note: Squirrel is the hostname of my Windows XP box.*

If I browse Places->Network->Windows Network->MSHOME->SQUIRREL, the Windows shares are seen but without a printer. Instead there is a networked folder named Print$ which I suspect is the printer being incorrectly recognized. I have attached an image of what I see.

**[COLOR="Red"]See workaround at post #10 below.[/COLOR]**

---

### Post by Salsero58 on 2009-04-30
You are not alone. I just installed Jaunty with the identical results. I can navigate to other areas on the network but the the printers cannot be located.
 
I notice that there have been no replies to your post, but was wandering if you have found a solution yet.

---

### Post by Circle of Owls on 2009-04-30
I had a similar problem - I wasn't able to see any of the shares on my XP machine and received the error "Unable to receive share list from server". I was able to get it working by entering the IP address of my XP machine into the "smb://" line of the printer setup dialog, then clicking on browse. Now the printer share name shows up correctly. This might be worth a try for your situation also.

I also had to setup the root password as it was disabled, and wouldn't accept the sudo password to complete the printer setup.

---

### Post by celem on 2009-04-30
The bug is, in my opinion, in SMBclient. I submitted a bug report (see link below). If any of you experience the same issue _please vote and or comment_ on the bug to elevate its priority.

See:
[http://tinyurl.com/djekwp](http://tinyurl.com/djekwp)

---

### Post by celem on 2009-04-30
I ran the Live-CD version of the 64 bit version of Ubuntu 9.04 as an experiment to see if the problem existed there also. This bug is **NOT **present in the 64-bit version. I can easily create a networked printer resident on a Windows XP machine on amb64 Ubunto 9.04. The SMBClient version is the same as in the 32-bit version.

Printing to my Windows printer is important to me so I may switch to amd64 Ubuntu 9.04 to escape this bug IF I can get Flash to work (seems to be a big issue with amb64). Besides, it gives me a reason to migrate to 64-bit.

---

### Post by Salsero58 on 2009-04-30
Circle,

This did the trick. Once I put in the IP address for the printer, Jaunty located the printer and quickly installed it.

Still it would nice if a fix can be put in place for this problem.

Thanks for tip.

Salsero58

---

### Post by bhaverkamp on 2009-05-01
I have the issue on one of my 64 bit systems. One was a clean install and has printer bug. The other was an upgrade and works.

> **celem said:**
> I ran the Live-CD version of the 64 bit version of Ubuntu 9.04 as an experiment to see if the problem existed there also. This bug is **NOT **present in the 64-bit version. I can easily create a networked printer resident on a Windows XP machine on amb64 Ubunto 9.04. The SMBClient version is the same as in the 32-bit version.

Printing to my Windows printer is important to me so I may switch to amd64 Ubuntu 9.04 to escape this bug IF I can get Flash to work (seems to be a big issue with amb64). Besides, it gives me a reason to migrate to 64-bit.

---

### Post by squirrelpie on 2009-05-02
Did a clean install of 9.04 on an old Dell Inspiron 1000 (2004-05)- Celeron w 512 ram, no wireless and PCMCIA ethernet adapter- that had Windows XP Home barely running. Was problematic in itself and would simply not install- crash after step 3 or 4- and then would not boot the Ubuntu CD only the HD inspite of proper BIOS setting until I used a disk utility to wipe out some of the hd. Then fine and installed and ran like a dream- very fast and much nicer interface than 8.**. Really an impressive release.Using Picasa3 and openoffice. Automatically found network connection and did updates. A couple of glitches with the display when I has dual monitor hooked up, but disappeared when I pulled the VGA cable. May be a hdwe prob with old machine. Not an issue at present. Much better video detection and choices than 8.**
Problem with printer shared on XP Pro Box same as others. Samba would simply terminate when browsing for printers. Solved by inputting 192.168.0.105 in the SMA address box and it brought up all my networked printers on whatever machines, plus identified all the boxes on my network Selected Lexmark0- a named printer which was an Optra S 1620 (MS) on parallel LTP1 and selected the Optra S 1250 Driver. Seems to be working like a charm. I'm not sure why the 192.168.0.5 works as I'm on DHCP on an old D Link 624 router (wired) but it does:)

---

### Post by cariboo on 2009-05-02
I just set up two printers, both networked to different computers. The ancient HP 5P connected to my server showed up automagically in the printer setup dialog. THe Epson R340 connected to a computer running XP, was also there when I selected the browse button. The only problem is that neither of the printers will print a test page, although any other page sent to either of them prints the way it should. I'm Running Karmic Koala, but right now there isn't to much difference between it and Jaunty.

---

### Post by celem on 2009-05-02
After reading the comments above, I too used my Windows box IP address instead of Browsing for the printer. This permitted me to go to the next steps and created a printer, although it didn't work, i.e. the test page didn't print. However, I then clicked the change URI button for the printer path name and it presented another opportunity to Browse. This time it found the Windows printer, correctly changed the path and then the test page printed.

I've attached a couple of snapshots.

---

### Post by celem on 2009-05-06
I used apport to grab the bug's crash and then reported it to launchpad, this time linking it to another existing bug report number 361629.  Other related bug reports are 329974, 344218, 359088, 360524. 

Of interest, I had previously successfully built a windows shared printer using the workaround that I described in my previous bug report, 368273, but attempted adding a second Windows shared printer while apport was running. The printer correctly appeared in the dialogue. When I deleted the printer and tried again, the bug reappeared, this time captured by apport.

---

### Post by lord_drake on 2009-05-07
i got that kind problem too...
plus this problem...
anybody can teach me how to solve this?
:(:(

---

### Post by celem on 2009-05-07
Your post-reply is not relevant to this post's problem. However, it appears that you must load the ML-4500 printer driver for the printing portion of your multi-function printer. See 
[http://tinyurl.com/dkwpne](http://tinyurl.com/dkwpne) 
and also 
[http://tinyurl.com/cx7hns](http://tinyurl.com/cx7hns) 
as well as 
[http://tinyurl.com/6y7evj](http://tinyurl.com/6y7evj)

---

### Post by sargetech on 2009-05-07
worked like a charm!!!
this method found both printers on my XP box
Very logical indeed!!!

Live Long and Prosper!!:guitar:

---

### Post by TageJensen on 2009-05-17
Thank you for the fix
Using Ubuntu Remix 9.04 on Dell Mini 9
Had same problem on all types of Ubuntu 9.04 but not on 8.04
Had all updates as of 17 May 2009
Installed Windows Printer via Samba
Type address in box, Installed fine, Testpage worked fine.
Installed XP Home shared printer, HP Laserjet 1010 , HP Photosmart 3110 all good.
 
Just an odd notice, this is the same problem if you try to add XP Home shared printer in WIN7
And the fix is the same.
Small world
 
Tage

---

### Post by TOfregato on 2009-06-06
Thanks, it worked for me too:

Linux Mint 7 on a old fujitsu-siemens amilo and HP Laserjet P1005 connected to a win 7 pc

Thank you again

---

### Post by Malfini on 2009-06-06
[SIZE=2]Hello All,

Total Noob here, struggling to set up a new system.

Entered[/SIZE][SIZE=2] IP address[/SIZE][SIZE=2] in "**smb://**" field, and it found the printer but won't print. I selected the recommended  driver (there are several) for the Brother HL-1440, but when I view printer properties [settings] I see:

**Printer state: Idle - Unable to connect to CIFS host, will retry in 60 seconds...**[/SIZE]

[SIZE=2]Suggestions? BTW I do see the WinXP computer in my network places.

A previous post mentioned telnet, how do i use it? 
[/SIZE][INDENT][SIZE=2]**"Hmm, check it with telnet:   $ telnet rinteserveripaddress 9100"**[/SIZE]

Thanks for any info
[/INDENT]

---

