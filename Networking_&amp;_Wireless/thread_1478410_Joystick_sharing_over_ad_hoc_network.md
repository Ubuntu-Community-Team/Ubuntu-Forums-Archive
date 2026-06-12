---
title: "Joystick sharing over ad hoc network"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by Peppr on 2010-05-09
Long time lurker here. I'm relatively new to Ubuntu/Linux and these forums have been an invaluable learning tool. However, I've stumbled on a problem to which I can't find a solution anywhere and I'm hoping someone here might be able to give some advice.

I am working on a project where I need a joystick connected to a local computer to register on a remote computer (both computers run Lucid). The goal is to SSH into the remote computer across an Ad Hoc network, and run successfully run jstest (CLI joystick testing program). The process I have been attempting is:

1. Set up an encrypted ad hoc network with 2 computers: a local box with a joystick attached, and a remote box with no joystick
2. From the local box, open a terminal and run "sudo ssh -X user@<remote_ip>" to SSH into the remote box
3. From the local box, send command "jstest <path_to_joystick>"

If step 3 is successful, then moving the joystick around should be reflected in the output from jstest. Unfortunately I have not been able to get this to happen.


Here are my troubleshooting steps:

- I have triple checked that the ad-hoc network is functioning properly, and successfully pinged each box.
- On each box, I installed jstest, physically connected the joystick and successfully ran the program, so I know there is no problem with the equipment.
- On the local box, I created a symlink from /dev/input/js0 to /home/<me>/Desktop/js0 and successfully ran "jstest /home/<me>/Desktop/js0", so I know that jstest accepts links to files


I have read that EVERYTHING is a file in Linux, so I thought maybe if I could get the two boxes to share /dev/input/js0, then jstest would successfully run across the network. I searched around a bit and came up with two possible methods: SSHFS and NFS. Here is what I did:

- I installed SSHFS to each box (and tested to ensure it functioned correctly). Then I tried mounting local:/dev/input to the remote box and creating a link from local:/dev/input/js0 to remote:/dev/input/js0.
- Opposite of above step. I mounted remote:/dev/input to the local box and created a link from local:/dev/input/js0 to remote:/dev/input/js0
- I tried repeating the above two steps using NFS instead of SSHFS.


Both SSHFS and NFS will allow me to create soft and hard links from local:/dev/input/js0 to remote:/dev/input/js0, but when I try step 3, I invariably get an error of some kind. It's been incredibly frustrating. I now have two questions:

Question 1: Is my understanding of "everything is a file in Linux" correct? Is my approach of sharing local:/dev/input/js0 appropriate? What do I not understand here?

Question 2: Is there ANY protocol/method/command/whatever that will allow the local and remote boxes to "share" the joystick over a network, or make the remote box think the joystick is physically attached?


Any help would be greatly appreciated. Thanks!

---

### Post by Peppr on 2010-05-10
Bump

---

### Post by Ollytheninja on 2010-09-04
Bump

Trying to do something much simpler and trying to find different options:
I want to control forward/next/pause/play in vlc from another PC, tried using python but aint getting anywhere.

Would really like to see you get this working

---

### Post by Peppr on 2010-09-04
I have not been able to get this working, but then again this is a side project of mine and I have been really busy. However, I have done more research and have found a few possible alternatives that might help.

From my project journal:

**Method 1: Create a Symbolic Link Across the Network** This would  link /dev/input/js0 on the localhost to /dev/input/js0 on the remote  host. The file on the remote will be called when jstest-gtk is run on  the remote machine. Some online research provided some possibilities: 
 
[LIST]
[*] **SSHFS:** SSH File System. A file system client to mount  and interact with directories and files located on a remote server or  workstation
[*] **NFS:** Network File System. Allows a user on a client  computer to access files over a network in a manner similar to how local  storage is accessed
[*] **USB/IP:** USB/IP Project aims to develop a general USB  device sharing system over IP network. To share USB devices between  computers with their full functionality, USB/IP encapsulates "USB I/O  messages" into TCP/IP payloads and transmits them between computers
[/LIST]
 **Method 2: Write a local program that uses ports to stream data over a network.**  This would require finding out how to send and receive packets of data  across the network via some sort of programming language (C, C+, C++,  etc). The receiving computer would have to have software that listens  for an incoming packet, interprets it, then performs some action based  on the data in the packet. It would then return a status packet which  the first computer would recognize. 



The USB/IP program is located at: [URL="http://usbip.sourceforge.net/"]http://usbip.sourceforge.net/
[/URL]
Here's a guide on network programming: [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)



If you get any of these to work for you, let me know!

---

### Post by Peppr on 2010-10-04
Finally had a chance to work on this some more. I installed usbip ([http://usbip.sourceforge.net/](http://usbip.sourceforge.net/))  to my laptop and desktop computers (both running Ubuntu 10.04). This  program was available in the Ubuntu repository and I was able to install  it using Synaptic.

**NOTE: This solution uses ssh ([https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)) and jstest-gtk ([http://www.getdeb.net/software/jstest-gtk](http://www.getdeb.net/software/jstest-gtk)). You should make sure that both jstest-gtk and the SSH-server are installed and working on the client computer ([https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)).**

The USB/IP protocol has two parts: a server and a client. The  server is  the machine to which the peripheral is physically attached and  the  client is the machine with the virtual connection. For the purposes of  these instructions, I made the laptop the server because that's where I  physically attached the  joystick. The client was my desktop computer.  These selections were arbitrary

After connecting the joystick to the laptop I opened up a terminal and ran:

```

sudo modprobe usbip              # Load the usbip module  
sudo modprobe usbip_common_mod   # Load the usbip_common_mod module
sudo modprobe vhci-hcd           # Load the vhci-hcd module
lsusb                            # Show list of of USB devices
```**lsusb** gives a list of all the USB devices attached to the computer, including the bus, device number and the ID:

```

Bus 007 Device 004: ID 04e8:681c Samsung Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 06a3:0160 Saitek PLC ST290 Pro
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root  hub
```This output shows that the joystick (Saitek PLC ST290 Pro) is  device 002 on bus 002. Its ID is 06a3:0160. This is the device that I  want to share with the remote computer, so I ran **sudo usbip_bind_driver --list** to get the bus-ID of the joystick. The output was: 

```

List USB devices
 - busid 3-1 (046d:c518)
         3-1:1.0 -> usbhid
         3-1:1.1 -> usbhid

 - busid 7-1 (04e8:681c)
         7-1:3.0 -> cdc_acm
         7-1:3.1 -> cdc_acm
         7-1:3.2 -> usb-storage
         7-1:3.3 -> none

 - busid 2-1 (06a3:0160)
         2-1:1.0 -> usbip
```The bus-ID for the joystick  (06a3:0160) is 2-1. I bound the joystick device to the server by  running:

```

sudo usbip_bind_driver --usbip 2-1
** (process:5099): DEBUG:  2-1:1.0    -> usbhid 
** (process:5099): DEBUG: unbinding interface
** (process:5099): DEBUG: write "add 2-1" to /sys/bus/usb/drivers/usbip/match_busid
** Message: bind 2-1 to usbip, complete!

usbipd -D      # Start the usbip daemon

ifconfig      # Show networking information
```Running **ifconfig** gave me the IP address of the laptop. I then moved to the desktop, opened up a terminal, then ran:

```

sudo modprobe usbip              # Load the usbip module  
sudo modprobe usbip_common_mod    # Load the usbip_common_mod module
sudo modprobe vhci-hcd            # Load the vhci-hcd module

sudo usbip -a <server-ip> 2-1     # Attach joystick
```I tested the set up by returning to the laptop and ran:

```

ssh -X *username*@<client_ip_address>
jstest-gtk
```This brought up the joystick testing GUI on the laptop.  When I moved the joystick around, the test program showed movement. The  response time was excellent. This is significant because the jstest-gtk  code was running on the remote computer even though the joystick was  attached locally.

---

