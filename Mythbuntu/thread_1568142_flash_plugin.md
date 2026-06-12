---
title: "flash plugin"
date: 2010-09-04
forum: Mythbuntu
---

### Post by slaterson on 2010-09-04
after installing mythbuntu on my new media pc, i noticed flash was not included.  after some searching, i discovered i needed to have 'ubuntu-restricted-extras' installed along with adobe-flash, of course.  so installed both of them, no errors or warnings.

i then tried viewing a web page with flash content in firefox as the root user.  it worked great.

then i tried the same thing as a regular user...  no luck.  firefox says the plugin is missing, i can go through and download/install it again via firefox, it simply says the plugin is already installed.  it still doesn't work, of course (only as root).

this seems to be a permissions issue for my user.  is there a group that my user(s) who need flash access should be added to?  what is it?

any help is appreciated!

thanks
slate

---

### Post by gordintoronto on 2010-09-04
The restricted extras includes flash, you should not need some other flash. Also, I suggest you never, ever do stuff as root. (I have not used mythbuntu, so perhaps it has some overwhelming reason to have a root userid.)

Having multiple flash programs is a problem, not a second chance for something good to happen.

---

### Post by kja999 on 2010-09-05
From memory there should be either a file or at least a symlink added into the users ~/.mozilla/plugins folder when flash is installed.
I think it used to be libflashplugin.so

There is a repository provided by Adobe which I use and I have forgotten about flash problems ever since ;)

---

### Post by slaterson on 2010-09-10
thanks kja999.  how do i go about adding the repository for adobe?

i checked for libflashplugin.so, my system only has libflashplayer.so and npwrapper.libflashplayer.so.  also, there is no plugins directory in the .mozilla directory, even on my gentoo systems where flash is working great for every user.

interesting, if i use the flash player as root, then logout and login as the mythtv user, it works.  if i reboot and go straight in as the mythtv user, its as if the plugin isn't installed.  also, in firefox, about:plugins reports there are NO plugins installed at all.

lastly, when i run the synaptics package manager gui as mythtv user, it prompts for the root password but the gui never opens.  as root, it works fine, of course.  is there perhaps a special group that the mythtv user needs to be a member of?  i am using ldap and have an entry for the mythtv user in my ldap directory, perhaps i missed something when adding the user?

---

### Post by LowSky on 2010-09-10
one You should never ever use root in Ubuntu based distro's. it makes things go a bit freaky.

that said go to adobe website, download the tar for flash, NOT the DEB turst me, unzip the tar and add the libflashplugin.so to ~./mozilla/plugins folder

---

### Post by slaterson on 2010-09-10
unfortunately that does not work. :(

i am not sure why there is so much concern about logging in as root to test things when something doesn't work.  i am new to ubuntu, though, but extremely familiar with gentoo.  and by no means am i running things as root on a regular basis, simply to try and address this flash issue.

very curious to me is the fact that firefox is saying there are NO plugins installed.  i've got nspluginwrapper installed and libflashplayer.

---

### Post by LowSky on 2010-09-10
Ubuntu based distro's use SUDO. root is disabled and unfortunatly when you enable it, and use it in a GUI setting things can go wrong and permissions often become messed up. I understand many other distros use root and it might be normal for you, but Its a strict rule around here to tell users that root is not a good idea to use, and to stick to sudo.

If I were you I would reisntall firefox. delete the .mozilla folder and reinstall. hopefully it works that way. and do so using sudo access not root.

---

### Post by slaterson on 2010-09-10
unfortunately that didn't work. :(

if i run firefox without sudo, firefox lists NO plugins are installed.  if i run 'sudo firefox', they are all listed.  this looks like a permissions issue to me, not sure where to look to fix it, though.  there is no plugins folder in the .mozilla directory.

i can see /usr/lib/flashplugin-installer/libflashplayer.so as a regular user.  permissions on the file are -rw-r--r--.  no execute.

---

### Post by JMcFly on 2010-09-10
Isn't it simply
> sudo apt-get install flashplugin-nonfree
?
 
I think thats all I had to do when I needed Flash to get Hulu Desktop and Youtube working in 10.04.

---

### Post by slaterson on 2010-09-10
> **JMcFly said:**
> Isn't it simply

```
sudo apt-get install flashplugin-nonfree
```

?
 
I think thats all I had to do when I needed Flash to get Hulu Desktop and Youtube working in 10.04.

it may very well be, but that isn't working for me.  the install worked without errors or warnings, however the plugin does not appear in firefox as any user unless i run firefox with sudo.

also, as mentioned previously, about: plugins in firefox states there are no plugins installed, when running sudo firefox it lists all the plugins as expected.

it really seems like this is permissions related, but not being familiar with ubuntu i am not sure where to look.  i have no 'plugins' directory in my .mozilla directories for any users on the system, adding one manually and copying the libflashplayer.so does not work, either.

---

### Post by goffa72 on 2010-09-11
I had troubles getting flash to work in mythbuntu 10.04 when installing boxee about 2 weeks ago. 

I found a few posts that did not fully help me but may work for you (i think these got flash in firefox working but not boxee)

[http://ubuntuforums.org/showthread.php?t=1533887](http://ubuntuforums.org/showthread.php?t=1533887)

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

I ended up downloading the deb file from adobe and installing that. This installed usr/lib/flashplugin-installer/libflashplayer.so

from memory I think I copied this file to /usr/lib/firefox-addons/plugins and also to ~/.mozilla/plugins

also /usr/lib/firefox-3.6.8 has a plugins directory linked to the firefox-addons/plugins directory.

when I type about:plugins in firefox address bar it points to ~/.mozilla/plugins/libflashplayer.so

Hope some of this helps you, I would probably try flash-aid first (one of the above posts).

Note smiley face above to be : p (without a space)

---

### Post by axelsvag on 2010-09-12
If you are using a 64 bit version you could try this. [HTML]http://queleimporta.com/finally-adobe-releases-native-64-bit-flash-10-for-linux/[/HTML] that has worked perfectly for me without doing anything special afterwards.

---

### Post by slaterson on 2010-09-12
thanks goffa and axel.  i'll take a look at and try all the suggestions, unfortunately i am away from the computer (business trip) and won't be able to do anything until saturday.

thanks!

---

