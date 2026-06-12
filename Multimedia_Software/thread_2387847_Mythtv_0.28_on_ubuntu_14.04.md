---
title: "Mythtv 0.28 on ubuntu 14.04"
date: 2018-03-24
forum: Multimedia Software
---

### Post by bilkay on 2018-03-24
My laptop is running ubuntu 14.04 with mythtv 0.27 installed. I recently upgraded my backend server to 16.04. In the process, the installed version of mythtv is now 0.28. I need to upgrade the laptop to 0.28, but after installing the 0.28 ppa, apt-get upgrade mythtv left it still at version 0.27. Am I missing something? Is there a way to ensure that it upgrades to a particular version?

---

### Post by Tadaen_Sylvermane on 2018-03-24
Is there a reason you don't upgrade the laptop to 16.04 as well? Only a year or so left before 14.04 goes eol anyway. no time like the present.

---

### Post by tinylagarto on 2018-03-24
I am not using 14.04 so I cannot guarantee how well the PPA works but if you add a PPA you first need to update and then dist-upgrade to be able to use the newer version:

```
 sudo apt-get update
```

then:

```
 sudo apt-get dist-upgrade
```

The command you used does not replace the older version.

---

### Post by bilkay on 2018-03-26
> **Tadaen_Sylvermane said:**
> Is there a reason you don't upgrade the laptop to 16.04 as well? Only a year or so left before 14.04 goes eol anyway. no time like the present.

Yes there is. I can't afford the hassle of an upgrade right now. In a month or so I can.

---

### Post by bilkay on 2018-03-26
> **ivanovnegro2 said:**
> I am not using 14.04 so I cannot guarantee how well the PPA works but if you add a PPA you first need to update and then dist-upgrade to be able to use the newer version:

```
 sudo apt-get update
```

then:

```
 sudo apt-get dist-upgrade
```

The command you used does not replace the older version.

Did that, still getting "MythTV Version : v0.27.6-18-gaba4858".

---

### Post by tinylagarto on 2018-03-26
What is the output of:

```
 apt-cache policy mythtv
```

---

### Post by bilkay on 2018-03-26
> **ivanovnegro2 said:**
> What is the output of:

```
 apt-cache policy mythtv
```


```
mythtv:
  Installed: 2:0.28.2+fixes.20180325.2d49bc1-0ubuntu0mythbuntu2
  Candidate: 2:29.1+fixes.20180322.bd764db-0ubuntu0mythbuntu4
  Version table:
     2:29.1+fixes.20180322.bd764db-0ubuntu0mythbuntu4 0
        500 http://ppa.launchpad.net/mythbuntu/0.29/ubuntu/ trusty/main i386 Packages
     2:0.29.0~master.20160509.0bfcd20-0ubuntu0mythbuntu3 0
        500 http://ppa.launchpad.net/mythbuntu/0.29/ubuntu/ trusty/main i386 Packages
     2:0.29.0~master.20160412.ea5fdd4-0ubuntu0mythbuntu3 0
        500 http://ppa.launchpad.net/mythbuntu/0.29/ubuntu/ trusty/main i386 Packages
 *** 2:0.28.2+fixes.20180325.2d49bc1-0ubuntu0mythbuntu2 0
        500 http://ppa.launchpad.net/mythbuntu/0.28/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     2:0.27.0+fixes.20140324.8ee257c-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse i386 Packages
     2:0.27.0+fixes.20140324.8ee257c-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse i386 Packages
```

---

### Post by tinylagarto on 2018-03-26
I see a lot of versions. Though install candidate is 29.1. and version 0.28 is already installed. 

What is the exact output of:

```
 sudo apt-get dist-upgrade
```

after you performed an update of all repositories?

What I do not get is that you want version 0.28 but it is installed though there is already a newer version as candidate. 

Probably we should also take a look at your sources list:

```
cat /etc/apt/sources.list
```

---

### Post by mörgæs on 2018-03-28
> **bilkay said:**
> I can't afford the hassle of an upgrade right now. In a month or so I can.

Looking through your threads it seems like upgrading old releases is a recurring problem. I suggest that you (in a month, when time permits) begin the habit of doing a clean install rather than upgrades. Saves a lot of time in the long run.

---

### Post by bilkay on 2018-03-30
> **mörgæs said:**
> Looking through your threads it seems like upgrading old releases is a recurring problem. I suggest that you (in a month, when time permits) begin the habit of doing a clean install rather than upgrades. Saves a lot of time in the long run.

I wish it were that simple. But thanks. Doing a clean install would be a lot simpler if I kept better records of all the extra stuff I install.

---

### Post by mörgæs on 2018-03-31
This is GNU/Linux. We don't keep track of installed packages by hand; it's done automatically. 

If you open [this thread]("https://ubuntuforums.org/showthread.php?t=1946145") and search for the word *get-selections* there is an option worth considering.

---

