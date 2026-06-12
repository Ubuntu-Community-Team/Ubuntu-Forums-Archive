---
title: "Easy networking?"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by Toshibawarrior on 2009-02-19
Hello all! I've been wondering for months if there's an easy way to connect to another computer on the same network...let's say like Remote Assistance did back in Windoze...

I'd like to access my mom's computer and help her fix stuff without going away from my laptop...I don't know if this could be possible since I'm using Kubuntu Intrepid and her computer is using Ubuntu Intrepid...

I wish there was a way to access both computers from one another and maybe listen to my music from the other computer and so on.

I'm a failure when it comes down to networking so any help will be greatly appreciated! ;)

Thanks in advance!

---

### Post by hobo on 2009-02-19
Here is a start. 

[http://www.linuxtopia.org/HowToGuides/VNC_setup_Linux_Windows.html]("http://www.linuxtopia.org/HowToGuides/VNC_setup_Linux_Windows.html")

---

### Post by Toshibawarrior on 2009-02-19
Thanks a lot!! This guide looks great! I'll try it out right away! ;)!

---

### Post by Toshibawarrior on 2009-02-19
Ok, I followed the guide completely but when I execute:
```

vncviewer localhost:1
```

I get my own desktop...what's up with that?......I don't want two minstances of my session...What did I do wrong?

By the way, not only does it display my own (my laptop's) session, it also displays it in horrible-mode...with extremely poor graphics and ugly looking colors...How can I fix all of this?...

Do I need to install tightvnc on both computers?...I feel so lost...lol!

Sorry for the array of stupid questions, but I want to learn all of this stuff...

---

### Post by Toshibawarrior on 2009-02-19
Update:Ok, now I understand why I got my session/desktop............I was stupid....But how the heck to I connect to the other computer on my network?...I have a router between both computers but I already forwarded port 5901...and NOTHING happens...I can establish ssh connections, I can view the remote desktop using vncviewer...I'm lost again...

Thanks in advance...

---

### Post by theozzlives on 2009-02-19
Why don't you just use remote desktop?

---

### Post by Toshibawarrior on 2009-02-20
Well, mostly because I'm using KDE and mom uses GNOME...so I want to learn how to connect to other computers using a standard method. 

Are my questions too hard to answer?...:(

---

### Post by hobo on 2009-02-21
> Update:Ok, now I understand why I got my session/desktop............I was stupid....But how the heck to I connect to the other computer on my network?...I have a router between both computers but I already forwarded port 5901...and NOTHING happens...I **can establish** ssh connections, I **can view the remote desktop** using vncviewer...I'm lost again...


What is it that you **can't** do? The above qoute is not clear to me.

---

### Post by Toshibawarrior on 2009-02-21
> **hobo said:**
> What is it that you **can't** do? The above qoute is not clear to me.

Ok, I can test the vncviewer with my own computer...I can make a "virtual" session of Kubuntu (my laptop on my laptop). But I can't connect to the other computer...a desktop using Ubuntu and connected through a router.

My laptop is connected via wireless and the desktop is connected with a LAN cable directly into the same router...

I'm sorry if I'm not clear enough, but I'm a failure with networking...Let me know if I need to explain a little more.

---

### Post by hobo on 2009-02-21
Have you started the vnc client on the other computer? can you ping it from your system?

---

### Post by Toshibawarrior on 2009-02-21
> **hobo said:**
> Have you started the vnc client on the other computer? can you ping it from your system?

Yeah I started it on both...but what is "ping it"?...

I can't even start and ssh connection between the computers...not to mention that I'm using the IP that the router says it has: 192.168.1.101...I don't know how to verify the computer's IP individually...

I use a Linksys WRT54GS router by the way...

---

### Post by hobo on 2009-02-21
Go to System/Administration/Network Tools and start the app. Then under the device tab select the interface you want to display. The IP information should then display the IP address. When you have the address for the the other computer (you need to do this from it) then use the Ping tab and input the IP address there and select ping. All this does is to try and communicate with the other computer. If both systems can see each other then we can go on. I have setup my systems so that we can work this out together.

---

### Post by hobo on 2009-02-21
I have my 2 systems working now with VNC. One is at 6.06 and the other at 8.10 and all is well. btw...one is wireless and the other hardwired

---

### Post by Toshibawarrior on 2009-02-21
Hmmm...I'm using Kubuntu on my laptop...but I also have Ubuntu on another partition...I'll go there and check it out...

---

### Post by hobo on 2009-02-21
You will have to allow remote connections from your mother's system by using System/Preferences/Remote Destop the fill in the blanks to allow the connection. See this:
 [http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html") 

Also when starting the connection from your laptop this is the syntax:

[I]NAME
       vncviewer - VNC viewer for X

SYNOPSIS
       vncviewer [options] [host][:display#]
       vncviewer [options] -listen [display#]

DESCRIPTION
       vncviewer  is  a  viewer  (client) for Virtual Network Computing.  This
       manual page documents the version for the X window system.

       If you run the viewer with no arguments it will prompt you  for  a  VNC
       server  to  connect  to.   Alternatively,  specify the VNC server as an
       argument, e.g.:

              vncviewer snoopy:2

       where ’snoopy’ is the name of the machine, and ’2’ is the display  num&#8208;
       ber of the VNC server on that machine.  Either the machine name or dis&#8208;
       play number can be omitted.  So for example ":1" means display number 1
       on  the  same  machine, and "snoopy" means "snoopy:0" i.e. display 0 on
       machine "snoopy".
[/I]

---

### Post by hobo on 2009-02-21
Ok forgot one system was Kubuntu. I have now booted to 8.10 Kubuntu
Check this out:
[http://http://kubuntuguide.org/Intrepid#Remote_Access]("http://http://kubuntuguide.org/Intrepid#Remote_Access")

This is for Kubuntu

---

### Post by Toshibawarrior on 2009-02-21
Thanks man! I wasn't able to reply quickly because my sister got a hold of my laptop and she was reading emails and stuff so I couldn't test the ping or anything. I'll check out your posts and reply back with the results!

Thanks again!

---

### Post by Toshibawarrior on 2009-02-22
Hmmm...still nothing...Not even in  Ubuntu-to-Ubuntu...

When I enter:

vncviewer <desktop-name>:1

it complains about not being able to convert the desktop's name into a hostname or something..............I feel nauseous...lol!...

I still have to read the guides you linked me carefully, I really feel like hammering both computers...:p!

---

### Post by hobo on 2009-02-22
OK here is what you need to do (kubuntu 8.10 to ubuntu 8.10):

1. Go to the system you want to remote into (ubuntu) and determine it's IP address.

2. While you are there, allow remote desktop access and use a password to protect that unit. Using the pull down SYSTEM/Preferences/Remote Desktop

3. At your Kubuntu Laptop using Konsole type:

   krdc vnc:/*yourmama's IP address*:1

4. The above command will start a program called KRDC. See:

[http://docs.kde.org/stable/en/kdenetwork/krdc/index.html]("http://docs.kde.org/stable/en/kdenetwork/krdc/index.html")
 
Select LAN,Direct Connection. Check mark both boxes in the host configuration dialog (remember password,etc)

5.  Whenever asked, enter the password

6, You should now be viewing *yourmamas* desktop via your laptop

---

### Post by hobo on 2009-02-22
When asked this: 

(vncviewer <desktop-name>:1) [I]I'm not sure why you are using that app. As I said in the previous append the app in KUBUNTU should be KRDC
[/I]
enter "vncviewer xxx.xxx.xxx.xxx:1" where xxx.xxx.xxx.xxx is the **IP address**, not the hostname, from the CMD below from the machine you want to connect to. Remember you **MUST allow** remote connections at the unit you want to connect to.

To determine the IP address type (ifconfig) on the terminal command line.
You should see something like this:

hobo@hobo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 
          inet addr:**192.168.1.1**  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr:                           Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3093686 (2.9 MiB)  TX bytes:5053069 (4.8 MiB)
          Interrupt:185

 The **BOLDED** number is the IP address of the unit you are on not the hostname.

---

### Post by Toshibawarrior on 2009-02-22
Thank you very much Hobo!!! I'll start working on this (again) in a few minutes! Thanks for your patience and easy-to-read guide! 

I'll come back (again) with the results! :popcorn:!

---

### Post by Toshibawarrior on 2009-02-22
SUCCESS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! (partially)

I finally could access my mom's computer, but as a separate session...

Isn't there a way to access the computer real-time, just like Remote Assistance did back in Windows...?

Maybe I'm asking too much, but I'd love that! Thanks for all you help, and if you do know how to achieve this, please do let me know! :)!

---

### Post by hobo on 2009-02-22
I am not sure what success you are having. If you followed the Kubuntu to Ubuntu directions above it will be realtime. What did you do and how did you do it?

---

### Post by Toshibawarrior on 2009-02-22
> **hobo said:**
> I am not sure what success you are having. If you followed the Kubuntu to Ubuntu directions above it will be realtime. What did you do and how did you do it?

Well...I started "vncserver" on Ubuntu (mom's comp) using tightvnc (I believe). And then on my laptop (Kubuntu) I entered:

```
krdc vnc:/192.168.1.101:1
```

on Konsole and it asked me the password and BOOM! my mom's desktop was here, but with no windows open...just the wallpaper and menus and stuff...the only realtime action I could do was turning off the computer......

Where did I go wrong?...Should I use tightvnc or not?...

If I don't input:

```
vncserver
```

on my mom's comp, KRDC says: Server Not Found.

Should I use another vnc client?

---

### Post by Toshibawarrior on 2009-02-22
I wish I could be able to share files and folders through the network too...is that possible?...

Again, I'm sorry for the array or stupid questions, but I know nothing about networking...:(!

---

### Post by hobo on 2009-02-22
You don't need to use anything other than whats built in to both distros.

Ubuntu to Ubuntu
1. On your machine use Remote Desktop Viewer
2. On the the other machine in Remote Desktop Preferences checkmark **both** Allow Others to view desktop and allow other to **CONTROL** the desktop. Under Security checkmark both fields and give it a password.
3. On your machine startup Remote Desktop Viewer under Applications/Internet and then fill in the blanks.

Kubuntu to Ubuntu
1. do step 2 above
2. The from the Kubuntu cmd line type : krdc vnc:/yourmama's IP address:1

If you have given permission to CONTROL the other desktop then should be able to do it

---

### Post by Toshibawarrior on 2009-02-22
> **hobo said:**
> 
Ubuntu to Ubuntu
1. On your machine use Remote Desktop Viewer
2. On the the other machine in Remote Desktop Preferences checkmark **both** Allow Others to view desktop and allow other to **CONTROL** the desktop. Under Security checkmark both fields and give it a password.
3. On your machine startup Remote Desktop Viewer under Applications/Internet and then fill in the blanks.

I tried it on Ubuntu and it says:

```
Connection to host "ivan-desktop.local:5900" was closed.
```

> 
Kubuntu to Ubuntu
1. do step 2 above
2. The from the Kubuntu cmd line type : krdc vnc:/yourmama's IP address:1

If you have given permission to CONTROL the other desktop then should be able to do it

I'm off to try this now...

---

### Post by Toshibawarrior on 2009-02-22
In Kubuntu it says:

Server Not Found

What should I do?...I believe I should have a VNC server running on Ubuntu. Do I?...

---

### Post by hobo on 2009-02-22
go ahead and start it up like you did when you where successfull

---

### Post by Toshibawarrior on 2009-02-22
Well, I did...and it's still the same...

I uninstalled tightvnc...but I installed vnc4server on Ubuntu...I still don't know why it doesn't let me connect without a vncserver.

What's weird is that Ubuntu uses DesktopDrapes (which changes the desktop's wallpaper every few minutes) and it changes the desktop here on my laptop...at the same time as on mom's computer...but I still can't control the desktop, or exchange files, or any other realtime actions...

Help?...

Do you think I shouldn't run "vncserver" on Ubuntu?...If I don't I get the errors I posted above.

---

### Post by hobo on 2009-02-22
Go ahead and start vncserver up. And make sure you have given permission to CONTROL under Remote Desktop Preferences

---

### Post by Toshibawarrior on 2009-02-22
When I start "vncserver" it says:

New "ivan-desktop:1 (ivan)" <---(whidch is the computer's name)

But I don't want a NEW thingy ... I want the session/desktop/thingy that's already opened there! :(!

Where did I mess up now?

---

### Post by hobo on 2009-02-22
Just start it up. Don't worry about that at this time

---

### Post by Toshibawarrior on 2009-02-22
Ok, it's up...Still no realtime movements...on my mom's computer the mouse laying dead...:(

---

### Post by hobo on 2009-02-22
Have you given permissions to CONTROL in System->Preferences->Remote Desktop ?

---

### Post by Toshibawarrior on 2009-02-22
> **hobo said:**
> Have you given permissions to CONTROL in System->Preferences->Remote Desktop ?

Yes I did...:(

Also, there's no sound here from the other computer and the video is sucky...like at 8-bit or something...I changed the setting on KRDC to 24-Bit and still looks sucky...:(

---

### Post by hobo on 2009-02-22
I sent you a PM

---

### Post by Toshibawarrior on 2009-02-22
Ok, thanks to Hobo I fixed this issue.

I installed x11vnc on both computers.

```
sudo apt-get install x11vnc
```

and I closed down all other vnc processes. Then I ran:
```

x11vnc
```

on a Terminal in Ubuntu and it shows a whole mess of output. it kinda logs everything you do every 2 seconds.

Then on Kubuntu I went to the Konsole and I entered:```


krdc vnc:/<mama's IP>:1
```

Entered the password when it prompted me to and VIOLA!

Everything works realtime! A little slow due to bandwidth issues but it's cool!!

This thread can be marked as SOLVED. But sadly that plugin was removed from the forums :(.

---

