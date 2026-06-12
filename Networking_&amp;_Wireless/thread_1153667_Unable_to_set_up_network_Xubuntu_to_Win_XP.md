---
title: "Unable to set up network Xubuntu to Win XP"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by TeachThai on 2009-05-09
I have two computers (one running Windows XP and the other running recent install of Xubuntu 9.04).  I can't set up the network between them although I had a good network between them when I had Windows 98SE connecting to the Windows XP computer.

One computer has AMD K6 processor - 118 Mb RAM - 6.0 Gb HD

Second computer has X86 Genuine Intel processor - 2393 Mhz - 512 Mb RAM - 28 Gb Free HD space

I have both computers connected to a router. The router is connected to my modem and I have Comcast connection to the modem.  As stated above, in the past I didn't have any problems setting up and using the same home network using the same two computers, router connections, and modem.

I have two icons showing up in the top right part of the screen on the computer with Ubuntu 9.04 running on it. Right clicking on the icons reveals a balloon saying I have an active wired connection.  Right clicking on the icon gives me stats about the connection such as interface number, hardware address, Broadcast address, subnet mask, default route, primary DNS, and Secondary DNS. I see that the router has given the Ubuntu running computer an IP address with one digit more than the Windows XP computer so I assume this has been assigned automatically by the router.  

I opened up the Windows XP network connection so I can see the name of the Windows XP based computer and the workgroup name on it.

When I opened up the "Remote Filesystems" (Gigolo) program to set up the connection between the two computers I see that the program has not detected the Windows XP computer.  I usually chose the Windows sharing option for the means of connecting. When I try typing in the Windows XP IP address and the folder path in the Windows XP computer the program says it can't find the shared folder.  I think this is the point where I am not typing in the correct information in the right places in the program that is supposed to help me set up the network.  I don't have much experience setting up networks because I have been able to do it easily in the past.

This is getting a bit frustrating because I have tried at least one other Linux distribution and also an Apple based laptop but I didn't have any trouble connecting to the Windows XP with those other operating systems although admittedly, I had more RAM in the laptop computers I have used in the past.

Thank you for any help you can provide.

---

### Post by dandnsmith on 2009-05-09
It sounds as if you've established that the IP addresses are commensurate, being something like 192.168.0.1, 192.168.0.2

The next thing to try is ping each way:
ping 192.168.0.1 from the 192.168.0.2 PC
and vice versa.
If these don't work then there is something like a firewall blocking, which you have to fix.
After that, it depends on how you're trying to 'share' the files or whatever.

---

### Post by TeachThai on 2009-05-09
Thank you for your reply Derek. I will try to "ping" the other computer. I will have to find out how to "ping" another computer.

---

### Post by TeachThai on 2009-05-09
Hi Derek,
Can you tell me how I should ping the other computer I am trying to network with?
Larry

---

### Post by superprash2003 on 2009-05-09
go to the Terminal ( Applications->Accessories->Terminal) and type ping 192.168.0.1

---

### Post by TeachThai on 2009-05-09
Thank you for your help.  I have downloaded the program called "Network Tools" and used the "ping" command from it to send packets to the computer with Windows XP on it.  All sent packages returned to me without errors.  Is there a way I can do the same from the computer with Win XP on it or is that not necessary?

---

### Post by TeachThai on 2009-05-09
Thank you for your note Prashanth.  I clicked on your link to your tech notes. They are very interesting. Thank you very much. I will bookmark them to refer to from time to time.  I see that you have notes on technology changes in India.  Do you know of any good sites that do the same things in Thailand?  I have an interest in Thailand because I lived there for quite a long time and I hope some day to go back there again to visit or perhaps to live there (in N. Thailand).
Larry

---

### Post by Iowan on 2009-05-09
> **TeachThai said:**
> Is there a way I can do the same from the computer with Win XP on it or is that not necessary?Going from weak memory... you should be able to click Start>Run, enter "cmd" (without quotes) to get to a command line.  **ping <address>** should give you information similar to  waht you've seen.

---

### Post by TeachThai on 2009-05-09
Thank you Iowan.  This procedure you gave me worked like a charm!  Now I know for sure that I have a good solid connection between the two computers.  Do you know what step I would do next to get the network going?
Larry

---

### Post by superprash2003 on 2009-05-10
im sorry i have no idea on thailand tech news.. Are you trying to access windows shared folders in ubuntu?? what are you typing to access them?something like smb://x.x.x.x/sharename ??have you enabled file sharing in windows?

---

### Post by TeachThai on 2009-05-10
Hi Prashanth.  Thank you for your help. Yes - I would like to be able to take files from the computer with XUbuntu on it and move / copy them to the computer with Windows XP on it.  I would also like to take the files from the Windows XP computer and move /copy them to the computer with Xubuntu on it.

I have enabled file sharing on the computer with Windows XP on it.  I have also gone into the Windows XP computer and made sure that even though the firewall is "ON" that the settings should allow for file sharing on a LAN between the two computers.

If needed, I am willing to go into the command line means of changing files and reading the settings in Linux rather than using the GUI form of making changes.  I just don't know at this point what to do next other than try to go into the Linux manual and figure out what commands I need to use to make any changes.

Thank you for your help.

---

### Post by TeachThai on 2009-05-10
Thank you for your note Prashanth.  Yes, I am trying to set up a LAN connection between my computer with  Xubuntu on in and my computer with Windows XP on it.  When I try to set up the connection to enable me to share files between the two computers I have gone into the computer with Windows XP on it to make sure that even though the "Firewall" is turned on, that it should still be able to share files on the LAN.  Then I go back to the computer with Xubuntu on it and open up the program called "Remote Filesystems" found in the "System" menu but it doesn't say that the computer with Xubuntu on it even sees the computer with Windows XP on it. When I am looking at a window where I have to type in the "Workgroup" or the SMB: address for the other computer I do that but I still am not able to make a connection.  Thus I go back to wondering what I should do next.  I have searched the forums quite a bit but I don't see anyone having success making a connection between the Xubuntu computers and a computer running Windows XP so I am ready to read up on the Linux manuals to see if there is any way for me to open up a terminal and go into the command line mode to call up any functions or to edit any files that are not being configured correctly.  Thank you for your help.
Have a good day there in India.
Larry

---

### Post by dandnsmith on 2009-05-12
To enable the access of files on the Xubuntu machine by Windows, you need to install SAMBA modules, and configure SAMBA.

The Synaptic package manager will do the package loading, if you set it to hunt for samba. Configuring the beast is a little more of an effort - there are various sites which offer tutorial and example material.

There is a guide to the whole lot [here](http://www.europe.eclipse.co.uk/Ubuntu)

---

