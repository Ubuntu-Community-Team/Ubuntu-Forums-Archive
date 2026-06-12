---
title: "Newbie, need help to share a folder and have it remain shared"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by charleswb on 2010-03-20
Every time I share a folder (using Ubuntu 9.10 Desktop), the share is gone after I reboot. How can I make it a permanent share that persists?

Note: I used the gui to create the share (if that matters).

Once I get the share permanent, the next thing I'll want to do is automatically mount it from another Ubuntu Desktop computer on the network.

Note: this will be a "peer to peer" network. I don't have Ubuntu Server and don't intend to get it. Just have two Ubuntu Desktop computers.

---

### Post by jrssystemsnet on 2010-03-20
```
you@box:~$ sudo apt-get update
you@box:~$ sudo tasksel install samba-server
```

OK, Samba's installed.  Now you need to add a share section for the folder in question.

```
you@box:~$ sudo nano /etc/samba/smb.conf
```

Tack this on to the end of the smb.conf file:

```
[myshare]
comment = this is my share.  there are many like it, but this one is mine.
path = /path/to/the/folder/I/wanna/share
writeable = yes
```

OK, that's the basics.  Now, do you want ANYBODY to be able to use this shared folder, no username and password required?  Then add this to your [myshare] block:

```
guest ok = yes
```

Or maybe you only want people to be able to access it if they have a valid username and a password... no problem; *don't* add the guest ok line.  But you'll need to set up a system account, and a samba account to match.  Which is easy enough.

```
you@box:~$ sudo useradd sambauser
you@box:~$ sudo smbpasswd -a sambauser
New SMB password:
Retype new SMB password:
```

Or if you want to use the same username you normally log in as (which will also help you avoid permission problems) do the same thing as above, but just skip the **useradd** step and go straight to the **smbpasswd** step.

---

### Post by charleswb on 2010-03-20
> **jrssystemsnet said:**
>  ```
you@box:~$ sudo apt-get update
you@box:~$ sudo tasksel install samba-server
```OK, Samba's installed.  Now you need to add a share section for the folder in question.

Did that ^ successfully.

> **jrssystemsnet said:**
> ```
you@box:~$ sudo nano /etc/samba/smb.conf
```Tack this on to the end of the smb.conf file:


I don't know what you mean by "tack this to end of smb.conf file". None the less, I typed that into the terminal, which started GNU nano 2.0.9 running. So what now?

> **jrssystemsnet said:**
> ```
[myshare]
comment = this is my share.  there are many like it, but this one is mine.
path = /path/to/the/folder/I/wanna/share
writeable = yes
```OK, that's the basics.

I don't understand where I'm supposed to enter that. In the regular Termnal window with GNU nano running, or in the Terminal window after closing GNU nano.

At this point I'm stuck with Terminal window running GNU nano and no idea how to proceed. It doesn't let me just type in the commands you gave, or I don't understand where to type them. In regular Terminal window, or in Terminal window running GNU nano?

No idea how to proceed.

---

### Post by charleswb on 2010-03-20
In desperation, I typed the following into Terminal Window with GNU nano program runnning.

[HostShare]
path = /home/charles/HostShare
writeable = yes

Then I pressed "Enter" key.

Then GNU nano asks "Save file under DIFFERENT NAME?" I don't know what I'm supposed to do then, but I guessed I wanted to save to same file name, but it won't let me. I tried to append file, but don't know how.

Am I supposed to append the smb.conf file? If so, how do I do so? The GNU namo samba program in terminal window says Append is M-A. How do I type M-A on keyboard? I tried that and it's not recognized.

Am I even supposed to be appending the smb.conf file with my share? Am I supposed to have my share configuration to a new file? I have no idea what to do.

---

### Post by charleswb on 2010-03-20
I just realized that the share is already created using smb by my VMware. My network is a host Ubuntu computer, and several VMware guest op systems, including several Windows guests and one Ubuntu guest.

Here is what I figured out. Although I had no luck creating a shared folder on the Ubuntu Desktop host, that's irrelevant because VMware had already created a Windows share on the Ubuntu host, and all my Windows guest op systems are already using it.

The problem I'm having is that my Ubuntu Guest doesn't allow me to mount the shared folder in the Ubuntu Host. I have no idea why My U guest can't mount the shared folder in the U host. 

However, the U guest can see the shared folder on the U host. Just can't mount it.

So what I really need to know is how to mount (from Guest Ubuntu) the shared folder on the Host Ubuntu.

---

### Post by SR_ELPIRATA on 2010-03-22
Charles:

When he says 'tack' he basically means to add that portion to the end of that file. Ever since the change into 9.04 sharing folders is a lot more work than before, setting shares on 7.10 was really easy and they simply screwed that up (IMO) in search of more security.

Security is always a good idea, but should be a good idea as well to at least have a guide somewhere where people can see how to share stuff easily. I can follow those terminal commands easily now, but when I started... I stayed away of those :)

Hope you make your shares work :)

ELP

---

