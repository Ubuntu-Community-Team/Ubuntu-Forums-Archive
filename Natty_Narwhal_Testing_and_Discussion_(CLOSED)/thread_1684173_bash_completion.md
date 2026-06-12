---
title: "bash completion"
date: 2011-02-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hugmenot on 2011-02-08
```
cd
ls Deskto<Tab><Tab>
```

I get 

```
ls Desktop
```

and not 

```
ls Desktop/
```

Anyone else?

---

### Post by MacUntu on 2011-02-08
The obvious question: do you have a file/directory starting with 'Desktop' in ~?

---

### Post by hugmenot on 2011-02-10
No no. It’s not about the particular folder. It’s that suddenly bash completion stopped to complete filenames for some commands.

I can’t smoothly Tab my way through the file system anymore.

Compare these:

```
cd Deskt<Tab><Tab>
ls Desk<Tab><Tab>
```

For the former it completes to "Desktop/", so you can continue on, for the latter it completes to "Desktop " so you have to backspace and add the slash manually.

Am I alone in this?

---

### Post by hugmenot on 2011-02-10
This bug seems to be it: [http://pad.lv/716008](http://pad.lv/716008)

---

### Post by mc4man on 2011-02-10
Works as expected here, adds /
 2 diff. installs, both fully updated

---

### Post by hugmenot on 2011-02-10
But do you have bash-completion on?

What happens if you type

```
sudo chm<Tab><Tab>
```

---

### Post by mc4man on 2011-02-10
> But do you have bash-completion on?
You can tell me, never really use (was trying what you've posted and expected, ect.
> What happens if you type sudo chm

First tab gives red, 2nd tab nothing happens (?), 3rd tab black, so complete is result of sudo chm<Tab><Tab><Tab>

```
doug@doug-alienware:~$ sudo chm[COLOR="Red"]od [/COLOR]
.adobe/                            .fontconfig/                       Music/
.bash_history                      .gconf/                            .nautilus/
.bash_logout                       .gconfd/                           .nvidia-settings-rc
.bashrc                            .gksu.lock                         .opera/
bin/                               .gnome2/                           opera_11.01.1190_i386.deb
.bogofilter/                       .gnome2_private/                   Pictures/
.cache/                            .gstreamer-0.10/                   .pki/
.cddbslave/                        .gtk-bookmarks                     .profile
.compiz/                           .gvfs/                             Public/
.config/                           .htoprc                            .pulse/
cpu3.log                           .ICEauthority                      .pulse-cookie
cpu.log                            .icons/                            .shotwell/
date.log                           .inputrc                           .sudo_as_admin_successful
.dbus/                             install_flash_player_10_linux.deb  Templates/
Desktop/                           .launchpadlib/                     .themes/
.dmrc                              .libreoffice/                      .thumbnails/
Documents/                         .local/                            Videos/
Downloads/                         .macromedia/                       .xsession-errors
.dvdcss/                           mem.log                            .xsession-errors.old
.esd_auth                          .mozilla/                          
examples.desktop                   .mplayer/                          
doug@doug-alienware:~$ sudo chmod
```

---

### Post by hugmenot on 2011-02-11
Hm odd. So you have bash completion on in .bashrc.

---

### Post by cariboo on 2011-02-11
The install I'm using at the moment is about 2 weeks old, bash completion works here the same way it works for mc4man. I have haven't done anything special.

---

### Post by mc4man on 2011-02-11
Interestingly enough Chris Coulson  has recently confirmed the bug you linked, I would certainly give weight there.

Personally can't see the described behavior on 2 different machines, no install less than a week old. If I did I guess the first thing I may try is to boot to the current iso and ck. 

The only other thing I've noticed in the past 12 wk.'s or so is some hardware acts differently and older installs + updates aren't always the same as a fresh one
(not to say they can't be..

edit; just did a fresh A2 on laptop - no issue here

---

### Post by hugmenot on 2011-02-11
Well, I downgraded to bash-completion 1:1.2-3ubuntu4. It works again. The new upstream release came Tue, 08 Feb 2011.

---

### Post by MacUntu on 2011-02-23
And the Oscar for the most annoying bug goes to... :D

Really, I thought the borked file rename highlight in Nautilus' list view was annoying, but this one really tops it.

---

### Post by portis on 2011-02-23
This turns out be to a bug of acroread package.
[http://aur.archlinux.org/packages.php?ID=16980](http://aur.archlinux.org/packages.php?ID=16980)

There's a workaround
sudo sed -i "s/_filedir/_filedir_acroread/" /etc/bash_completion.d/acroread.sh

---

### Post by MacUntu on 2011-02-23
Duuuuude, how could I miss that information... thanks! That's probably why it's not yet fixed. !:-)

---

