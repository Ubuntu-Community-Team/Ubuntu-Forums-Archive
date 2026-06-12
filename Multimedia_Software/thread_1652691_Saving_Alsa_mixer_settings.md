---
title: "Saving Alsa mixer settings"
date: 2010-12-25
forum: Multimedia Software
---

### Post by squrl on 2010-12-25
xxx

---

### Post by lidex on 2010-12-25
The command to save alsamixer settings is:
```
sudo alsactl store 0
```
If that doesn't work, open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

---

### Post by squrl on 2010-12-25
xxx

---

### Post by lidex on 2010-12-25
You're welcome. Enjoy.

---

### Post by fabio.hipolito on 2011-03-15
Hi to all,

I have followed Lidex's solution but at least the input source always changes from Front Mic to Mic.

Thank you and best regards,
Fábio Hipólito.

---

### Post by lidex on 2011-03-18
> **fabio.hipolito said:**
> Hi to all,

I have followed Lidex's solution but at least the input source always changes from Front Mic to Mic.

Thank you and best regards,
Fábio Hipólito.

Remove your pulse configuration files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

Now set your mixer levels and repeat saving:
```
sudo alsactl store 0
```

---

### Post by ghormax on 2011-05-05
I get the message: 

Home directory /home/myusername not ours.

What did I do wrong?

---

### Post by Yellow Pasque on 2011-05-05
It is a serious permissions issue unless you literally typed 'myusername' instead of your actual username. Check permissions with:
```
ls -la
```

---

### Post by fabio.hipolito on 2012-04-04
Hi,

first thank you for the replies and sorry for my very late reply.

Lidex I proceded as you recomended and I got
```
julia@owl:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
rm: cannot remove `/home/julia/.asound*': No such file or directory
julia@owl:~$ sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory

```

I logged out and in, after that I reajusted the alsamixer levels, i.e. changed the input from Mic to Front Mic

and then
```
julia@owl:~$ sudo alsactl store 0
[sudo] password for julia: 
Home directory /home/julia not ours.

```
the same problem as ghormax, but the premission seem to be correct
```
julia@owl:/home$ ll
total 12
drwxr-xr-x  3 root  root  4096 2012-01-09 10:19 ./
drwxr-xr-x 23 root  root  4096 2012-04-04 22:50 ../
drwxr-xr-x 28 julia julia 4096 2012-04-04 23:47 julia/
julia@owl:/home$ cd ~
julia@owl:~$ ll
total 192
drwxr-xr-x 28 julia julia  4096 2012-04-04 23:47 ./
drwxr-xr-x  3 root  root   4096 2012-01-09 10:19 ../
drwx------  4 julia julia  4096 2012-01-09 13:18 .adobe/
-rw-------  1 julia julia  2147 2012-04-04 23:48 .bash_history
-rw-r--r--  1 julia julia   220 2012-01-09 10:19 .bash_logout
-rw-r--r--  1 julia julia  3353 2012-01-09 10:19 .bashrc
drwx------ 14 julia julia  4096 2012-01-12 13:54 .cache/
drwx------ 14 julia julia  4096 2012-04-04 23:40 .config/
drwx------  3 julia julia  4096 2012-01-09 11:06 .dbus/
drwxr-xr-x  2 julia julia  4096 2012-01-09 13:18 Desktop/
-rw-rw-r--  1 julia julia    26 2012-04-04 23:37 .dmrc
drwxr-xr-x  2 julia julia  4096 2012-01-09 11:06 Documents/
drwxr-xr-x  2 julia julia  4096 2012-01-09 12:41 Downloads/
-rw-------  1 julia julia    16 2012-01-09 11:06 .esd_auth
-rw-r--r--  1 julia julia   179 2012-01-09 10:19 examples.desktop
-rw-r--r--  1 root  root  19420 2012-01-09 10:16 .face
drwxr-xr-x  2 julia julia  4096 2012-01-09 13:14 .fontconfig/
drwx------  5 julia julia  4096 2012-04-04 23:37 .gconf/
-rw-r-----  1 julia julia     0 2012-04-04 22:51 .gksu.lock
drwx------  4 julia julia  4096 2012-01-09 11:07 .gnome2/
drwx------  2 julia julia  4096 2012-01-09 11:06 .gphoto/
drwxrwxr-x  2 julia julia  4096 2012-01-12 13:54 .gstreamer-0.10/
-rw-rw-r--  1 julia julia   137 2012-04-04 23:37 .gtk-bookmarks
dr-x------  2 julia julia     0 2012-04-04 23:37 .gvfs/
-rw-------  1 julia julia  6732 2012-04-04 23:37 .ICEauthority
drwxrwxr-x  3 julia julia  4096 2012-01-09 11:06 .local/
drwx------  3 julia julia  4096 2012-01-09 11:24 .macromedia/
drwx------  3 julia julia  4096 2012-01-09 11:06 .mission-control/
drwx------  4 julia julia  4096 2012-01-09 11:23 .mozilla/
drwxr-xr-x  2 julia julia  4096 2012-01-09 11:06 Music/
drwxr-xr-x  2 julia julia  4096 2012-01-09 11:06 Pictures/
-rw-r--r--  1 julia julia   797 2012-04-04 23:22 .profile
drwxr-xr-x  2 julia julia  4096 2012-01-09 11:06 Public/
drwx------  2 julia julia  4096 2012-04-04 23:47 .pulse/
-rw-------  1 julia julia   256 2012-04-04 23:47 .pulse-cookie
drwx------  6 julia julia  4096 2012-04-04 23:10 .Skype/
-rw-r--r--  1 julia julia     0 2012-01-09 11:11 .sudo_as_admin_successful
drwxr-xr-x  2 julia julia  4096 2012-01-09 11:06 Templates/
drwx------  3 julia julia  4096 2012-01-09 13:18 .thumbnails/
drwxr-xr-x  2 julia julia  4096 2012-01-09 11:06 Videos/
drwxrwxr-x  4 julia julia  4096 2012-01-09 13:29 .wine/
-rw-------  1 julia julia    48 2012-04-04 23:37 .Xauthority
-rw-------  1 julia julia 12499 2012-04-04 23:41 .xsession-errors

```

Any thoughts?

Best regards.

---

### Post by fabio.hipolito on 2012-04-04
Hi,

me again, after rebooting I tryied again to edit alsamixer and save. It keeps not saving, but no longer complains about the ownership of the home folder.

Cheers.

---

