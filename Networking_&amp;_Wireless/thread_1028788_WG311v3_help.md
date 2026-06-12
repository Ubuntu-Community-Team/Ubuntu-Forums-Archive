---
title: "WG311v3 help"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by ididntdoit52 on 2009-01-02
Alright so I'm a newbie to linux and I can't figure out how to get my network adapter (the Netgear WG311v3) to work. I'm pretty sure I have to use ndiswwrapper but I can't figure out how it works. So can anyone link me a guide or explain how to get this damn card to work? And remember I'm new to linux so your gonna have to speak slowly and use small words ;)

inb4 google. I spent all last night looking for guides and threads.

---

### Post by melojo on 2009-01-02
open a terminal and post the output of

```
lspci
sudo lshw -C netowrk
ifconfig
uname -rm

```

this will give us more info

---

### Post by ididntdoit52 on 2009-01-02
Wow. Ubuntu forums are fast. Alright gimme a second, I'm trying to get my mouse working now.:sad:

---

### Post by ididntdoit52 on 2009-01-02
Ok here they are.

---

### Post by ididntdoit52 on 2009-01-02
bump

---

### Post by melojo on 2009-01-02
What I understand about this device is that you need to use ndiswrapper with windows xp driver.

I have to leave for a little bit and after I get back I will type out what to install.

If someone else wants to help please chime in.  If no one asnwers the post for an a couple of hours or so I would bump it.

---

### Post by ididntdoit52 on 2009-01-02
bump

---

### Post by impalerau on 2009-01-03
OK, I just did this last night to replace a card I was having problems with...

First find the Windows XP drivers folder on your Netgear CD and copy all the files to your desktop.  Then follow these instructions...

    1. Open a terminal window (Applications -> Accessories -> Terminal). In the window, type the following to switch to the directory containing the driver files:

    ```
cd /home/<username>/Desktop

```
    Replace <username> with your own username.

    2. To install the driver, type the following:

    ```
sudo ndiswrapper -i filename.inf
```

    Replace filename.inf with the name of the .inf file you discovered in the previous steps.

    3. Next, type the following:

    ```
sudo ndiswrapper -m
```
    ```
gksu gedit /etc/modules
```

    This will open the modules configuration file for editing. On a new line at the bottom, add the following:

    ```
ndiswrapper
```

    Ensure you press Enter after adding the line.

    4. Save the file, close Gedit, and reboot your computer.

Only thing left then is to delete the files from your desktop.

Let me know how you go.

---

### Post by ididntdoit52 on 2009-01-03
> **impalerau said:**
> OK, I just did this last night to replace a card I was having problems with...

First find the Windows XP drivers folder on your Netgear CD and copy all the files to your desktop.  Then follow these instructions...

    1. Open a terminal window (Applications -> Accessories -> Terminal). In the window, type the following to switch to the directory containing the driver files:

    ```
cd /home/<username>/Desktop

```
    Replace <username> with your own username.

    2. To install the driver, type the following:

    ```
sudo ndiswrapper -i filename.inf
```

    Replace filename.inf with the name of the .inf file you discovered in the previous steps.

    3. Next, type the following:

    ```
sudo ndiswrapper -m
```
    ```
gksu gedit /etc/modules
```

    This will open the modules configuration file for editing. On a new line at the bottom, add the following:

    ```
ndiswrapper
```

    Ensure you press Enter after adding the line.

    4. Save the file, close Gedit, and reboot your computer.

Only thing left then is to delete the files from your desktop.

Let me know how you go.

Well that solves one of my problems, but my other problem is I don't have the Netgear CD anymore so I had to download the drivers off of Netgear's site. The driver file is an .exe and I have no idea how to "extract it". Thanks for the info on ndiswrapper though. :D

---

### Post by melojo on 2009-01-03
Sorry it took me so long to get back.

Lets do this 1 step at a time.

Since you don't have internet working on that machine we will need to install ndiswrapper from the cdrom, so boot into ubuntu and put in the cd and close the dialogue box that opens.

Now

goto system>administration>synaptic package manager>settings>repositories
down at the bottom you will see a box that says cdrom with ubuntu 8.10 check the box. Now close it then in the upper left corner you will see reload, click it.

Now do a search for ndiswrapper and install ndiswrapper-common and ndiswrapper-utils-1.9

---

### Post by melojo on 2009-01-03
since impalerau has done it recently I am going to let him take over.

---

### Post by ididntdoit52 on 2009-01-03
> **melojo said:**
> Sorry it took me so long to get back.
Not a problem. :D

> **melojo said:**
> Lets do this 1 step at a time.

Since you don't have internet working on that machine we will need to install ndiswrapper from the cdrom, so boot into ubuntu and put in the cd and close the dialogue box that opens.

Now

goto system>administration>synaptic package manager>settings>repositories
down at the bottom you will see a box that says cdrom with ubuntu 8.10 check the box. Now close it then in the upper left corner you will see reload, click it.

Now do a search for ndiswrapper and install ndiswrapper-common and ndiswrapper-utils-1.9
When I hit reload it says "Could not download all repository indexes The Repository may no longer be available or could not be  contacted because of network problems. Blah blah blah..."
and when I search for ndiswrapper nothing comes up. :confused:

---

### Post by ididntdoit52 on 2009-01-03
However, I do have the 1.52 version of both the common and the utils .deb files. Would that work?

---

### Post by impalerau on 2009-01-03
Gee thanks, melojo :)

Ok, ididntdoit52.  The instructions I gave you came from a post of mine from a little over a year ago when I first got involved with Linux.  in that post i credit this site: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

It's an extract of the ndiswrapper chapter of a Linux reference book.  This is where I finally got the info I needed to get my wireless set up.  There's a section there about how to extract the files from a downloaded driver .exe which will probably help you.  I haven't had to do that myself though.  

I've got a copy of the driver disk but I'm not sure about the rules regarding posting proprietary drivers here.

Good luck.  I'll check in shortly to see how you got on.

---

### Post by melojo on 2009-01-03
> **ididntdoit52 said:**
> However, I do have the 1.52 version of both the common and the utils .deb files. Would that work?

So then you have ndiswrapper installed?

here is a link to the driver.

[ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)

after download put it in your home directory and unzip. It should extract in its own directory under your home.

---

### Post by ididntdoit52 on 2009-01-03
> **melojo said:**
> So then you have ndiswrapper installed?

here is a link to the driver.

[ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)

after download put it in your home directory and unzip. It should extract in its own directory under your home.
I'm not sure to be honest. I extracted both files in home, if that means its installed then yes, yes I do! :D

---

### Post by impalerau on 2009-01-03
> **ididntdoit52 said:**
> Not a problem. :D


When I hit reload it says "Could not download all repository indexes The Repository may no longer be available or could not be  contacted because of network problems. Blah blah blah..."
and when I search for ndiswrapper nothing comes up. :confused:

I had the same hassle last night.  I got around it as follows:

1. insert your Ubuntu install CD into the drive

2. Open Synaptic Package Manager

3. Go Settings/Repositories
 
4. Go to the Third-Party Software tab

5. De-select everything

5. Click the Add CD-ROM button and refresh.

You should then have the ndiswrapper packages available to install.

after you get your network iup you can go back to Synaptic, remove the extra CD-ROM entry and re-enable you original selections.

---

### Post by melojo on 2009-01-03
> **impalerau said:**
> I had the same hassle last night.  I got around it as follows:

1. insert your Ubuntu install CD into the drive

2. Open Synaptic Package Manager

3. Go Settings/Repositories
 
4. Go to the Third-Party Software tab

5. De-select everything

5. Click the Add CD-ROM button and refresh.

You should then have the ndiswrapper packages available to install.

after you get your network iup you can go back to Synaptic, remove the extra CD-ROM entry and re-enable you original selections.

I forgot you need to open a terminal and type

```
sudo apt-cdrom add 
```

that should fix it, it should open a dialogue box.

---

### Post by melojo on 2009-01-03
ok I am going to but out and let impalerau take care of you.

later guys

---

### Post by ididntdoit52 on 2009-01-03
> **melojo said:**
> ok I am going to but out and let impalerau take care of you.

later guys
Thanks for the help melojo.

---

### Post by ididntdoit52 on 2009-01-03
> **impalerau said:**
> I had the same hassle last night.  I got around it as follows:

1. insert your Ubuntu install CD into the drive

2. Open Synaptic Package Manager

3. Go Settings/Repositories
 
4. Go to the Third-Party Software tab

5. De-select everything

5. Click the Add CD-ROM button and refresh.

You should then have the ndiswrapper packages available to install.

after you get your network iup you can go back to Synaptic, remove the extra CD-ROM entry and re-enable you original selections.
Alright I have it installed.

---

### Post by impalerau on 2009-01-03
> **ididntdoit52 said:**
> Alright I have it installed.

Great.  Is that just ndiswrapper or the drivers as well?

---

### Post by ididntdoit52 on 2009-01-03
> **impalerau said:**
> Great.  Is that just ndiswrapper or the drivers as well?
Just ndiswrapper unfortunately. Still working on the drivers.

---

### Post by ididntdoit52 on 2009-01-03
I got it all working! Thank you VERY much to melojo impalerau for all the help you guys gave me. :D Now lets see if I can get the drivers for my graphics card. :P

---

