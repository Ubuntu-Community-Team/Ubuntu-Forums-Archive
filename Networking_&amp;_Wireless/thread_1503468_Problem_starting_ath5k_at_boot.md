---
title: "Problem starting ath5k at boot"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by damontallen on 2010-06-06
For the last couple days I've been working on getting my wife's Toshiba Satellite working under Ubuntu 10.04.  The only real problem I was having is that her wireless internet connection would slow down to a crawl.  I finally got it working by installing the proprietary version of ath5k following these [[COLOR="Blue"]instructions[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros").  I used the "Manually installed drivers" option 2.  The only issue I have now is that every time I boot up I have to manually restart ath5k using "sudo modprobe ath5k nohwcrypt=1" found in another post (not sure where).  How I can get ath5k to load automatically?

---

### Post by damontallen on 2010-06-07
After fixing my typo I found this 

install modulenamecommand...
    This is the most powerful primitive in modprobe.conf: it tells modprobe to run your command instead of inserting the module in the kernel as normal. The command can be any shell command: this allows you to do any kind of complex processing you might wish. For example, if the module "fred" worked better with the module "barney" already installed (but it didn't depend on it, so modprobe won't automatically load it), you could say "install fred /sbin/modprobe barney; /sbin/modprobe --ignore-install fred", which would do what you wanted. Note the --ignore-install, which stops the second modprobe from re-running the same install command. See also remove below.

    You can also use install to make up modules which don't otherwise exist. For example: "install probe-ethernet /sbin/modprobe e100 || /sbin/modprobe eepro100", which will try first the e100 driver, then the eepro100 driver, when you do "modprobe probe-ethernet".

    If you use the string "$CMDLINE_OPTS" in the command, it will be replaced by any options specified on the modprobe command line. This can be useful because users expect "modprobe fred opt=1" to pass the "opt=1" arg to the module, even if there's an install command in the configuration file. So our above example becomes "install fred /sbin/modprobe barney; /sbin/modprobe --ignore-install fred $CMDLINE_OPTS" 

at [http://linux.die.net/man/5/modprobe.conf](http://linux.die.net/man/5/modprobe.conf)

and I am wondering could I load ath5k by adding

Install ath5k

to the /etc/modprobe.d/alsa-base.conf file?  Do all of the files in /etc/modprobe.d load at boot?  Should I just try this or is there some other syntax that I should add?

---

### Post by damontallen on 2010-06-07
Never mind I found the solution here [[COLOR="Blue"]http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9026676&postcount=19[/COLOR]]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9026676&postcount=19")

---

### Post by damontallen on 2010-06-07
The full process was pieced together in this order.
```
sudo apt-get install build essential
```

Then from [[COLOR="Blue"]http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6[/COLOR]/]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/ ")

I downloaded the current madwifi-hal-0.10.5.6-r*.tar.gz	file.  (This was madwifi-hal-0.10.5.6-r4126-20100324.tar.gz at the time.)  Then in the download directory I continued with.

```
tar -zxvf madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
cd madwifi-hal-0.10.5.6-r*
sudo make
sudo make install
sudo su
     echo ath5k >> /etc/modules
     exit
sudo make clean
```

This fixed my wifi but I may have to re-make the file when the linux headers are updated.  This was gathered from the links posted in the previous posts.

---

