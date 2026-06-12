---
title: "SSH works from terminal, not from GNOME"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by SpindizZzy on 2013-02-24
I have two Ubuntu boxes set up: one running 12.04 Server and one running the standard desktop version of 12.04, with GNOME.


  I can ssh into my server computer from my desktop using terminal using ```
ssh spin@192.168.0.xxx -p 22
```  but when I try to do the same thing from my GNOME desktop (using 'File  > Connect to Server') I immediately get "connection refused by  server".


  In the dialog box I use the same port number (22), the same user  (spin), the same IP address and select 'SSH'.  I leave the 'folder'  option as '/'.


  What am I missing?

---

### Post by ahallubuntu on 2013-02-24
~

---

### Post by SpindizZzy on 2013-02-24
Thanks ahallubuntu for your speedy reply.

I think i correctly enter the data in the dialog box (see attached screenshot)  so I'm guessing something else is wrong. 

Is there a way to get a verbose output of this process, so I can see WHY the connection is refused ?

Is GNOME perhaps using a different authentification set ?

---

### Post by Morbius1 on 2013-02-24
>  Is there a way to get a verbose output of this process, so I can see WHY the connection is refused ?The closest thing I can think of is this:
```
gvfs-mount ssh://spin@192.168.0.xxx -vvv
```Connecting via Nautilus or "Connect to Server" is a gvfs thing so this is close. The "-vvv" is verbose mode.

---

### Post by SpindizZzy on 2013-02-25
Thanks Morbius1 to try to help solve this annoying glitch :)

```
gvfs-mount ssh://spin@192.168.0.xxx -vvv

```gives 

```
Error mounting location: volume doesn't implement mount
Error mounting location: Connection refused by server
```Does that help to solve my issue ?

---

### Post by schragge on 2013-02-25
Does *sftp* from terminal work?
```

sftp spin@192.168.0.xxx

``` I guess *gvfs-mount* actually uses sftp on port 115 even if it spells the protocol ssh://

---

### Post by SpindizZzy on 2013-02-25
Thank you schragge for joining the discussion :P

And yes, that command works. This is the output:
```
Connected to 192.168.0.xxx.
sftp> ls
Desktop                   Documents                 Downloads                 
Firefox_wallpaper.png     Music                     Pictures                  
Public                    Templates                 Videos                    
sftp>
```
I also discovered that when i use this line in terminal, my remote HD gets mounted  locally (without havinfg to enter my 'remote' user's password) and I can access it:
```
sshfs -o idmap=user spin@192.168.0.xxx:/media/604 ~/L -p 5901

```BUT when I put that same line in rc.local, to make that HD mount every time i boot my desktop, I get prompted for a password. Upon entering that, the disk gets mounted, but i get a dialog box when i try to open the drive. See attached screenshot.

I am now leaning towards a 'permissions'-difference between mounting from terminal and mounting through rc.local. 
How do I work around this or change permissions so that this line in rc.local works ?

All help more than welcome :P

---

### Post by schragge on 2013-02-25
rc.local gets executed as root with SSH settings for the root user (/root/.ssh/). Thus, if you have keys defined in ~/.ssh/ then SSH won't see them.

---

### Post by SpindizZzy on 2013-02-27
Ok, i see where the problem lies, but after some fiddling around haven't found what to do ... :(
  
Where exactly do I have to add the keys ? On my desktop PC, right ? Where to find that hidden ssh-folder ?

---

### Post by schragge on 2013-02-27
Well, you can try
```

sudo -u username sshfs -o idmap=user spin@192.168.0.xxx:/media/604 ~/L -p 5901

``` from rc.local.

Alternatively, you can put the command into some startup file that gets executed as normal user: ~/.xsessionrc, ~/.gnomerc, whatever.

---

