---
title: "Mythtv update keeps repeating"
date: 2011-01-18
forum: Mythbuntu
---

### Post by milesnorth on 2011-01-18
I have Kubuntu 10.10 with Mythtv .24.  Downloaded the latest updates of Mythtv with 21 update components through Kpackagekit twice now.  The same updates have now shown up for a third time.  Have the description of one of the updates below.

Updates:
• libmyth-0.24-0 - 2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2
 Repository: maverick

What might be done to figure out what is going on with these multiple updates and am I even in the right section of the forum?

Thanks for any info,
Kurt

---

### Post by tgm4883 on 2011-01-19
> **milesnorth said:**
> I have Kubuntu 10.10 with Mythtv .24.  Downloaded the latest updates of Mythtv with 21 update components through Kpackagekit twice now.  The same updates have now shown up for a third time.  Have the description of one of the updates below.

Updates:
• libmyth-0.24-0 - 2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2
 Repository: maverick

What might be done to figure out what is going on with these multiple updates and am I even in the right section of the forum?

Thanks for any info,
Kurt

I'm not familiar with kpackagekit, but I would check to see if you have that version installed.

---

### Post by milesnorth on 2011-01-19
> **tgm4883 said:**
> I'm not familiar with kpackagekit, but I would check to see if you have that version installed.

Package manager shows mythtv update version:
• libmyth-0.24-0 - 2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2

~$ mythfrontend --version
Please attach all output as a file in bug reports.
MythTV Version   : v0.24-101-gc6c50df
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0

Not really sure how to tell if these two versions are a match?  They look very similar.

---

### Post by nickrout on 2011-01-19
```
dpkg -l mythtv-frontend
```

You seem to have mythbuntu-repos installed (you need to to get 0.24). If so, you will get updates every day sometimes.

---

### Post by milesnorth on 2011-01-20
> **nickrout said:**
> ```
dpkg -l mythtv-frontend
```You seem to have mythbuntu-repos installed (you need to to get 0.24). If so, you will get updates every day sometimes.

A brief history:
I initially was not sure how to install mythtv and remember going to the download area of mythtv.org and clicking on a couple of links.  Probably downloaded some repository stuff there.  Then I decided not to continue there and next did an apt-get install for mythtv 0.23.  Mythtv was working well for the next few months so I went to the control center and upgraded to mythtv 0.24.

~$ dpkg -l mythtv-frontend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
ii  mythtv-frontend      2:0.24.0+fixes.20110 A personal video recorder application (client)


list of other software sources enabled:
[http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu)
[http://ppa.launchpad.net/mythbuntu/0.24/ubuntu](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu)
[http://ppa.launchpad.net/mythbuntu/0.24/ubuntu](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu) 

Do I remove the above sources and add other appropriate mythtv sources?  

Thanks for the observations and any more tips to help straighten my mess out.

---

### Post by nickrout on 2011-01-20
Unfortunately the output has been cut off without all the version details. Try:```
sudo aptitude install mythtv-frontend -V
```Then press n - but post back the results.

---

### Post by milesnorth on 2011-01-21
Hopefully this helps.

~$ sudo aptitude install mythtv-frontend -V

The following packages will be upgraded: 
  
  libmyth-0.24-0 [2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 -> 2:0.24.0+fixes.20110120.90fe13c-0ubuntu0mythbuntu2]  
  mythtv-frontend [2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 -> 2:0.24.0+fixes.20110120.90fe13c-0ubuntu0mythbuntu2]  
  
Likely not much help, but Apt-get upgrade shows these 21 packages:

The following packages will be upgraded:
  libmyth-0.24-0 libmyth-python libmythtv-perl mytharchive mythbrowser mythmusic mythnetvision mythtv
  mythtv-backend mythtv-common mythtv-database mythtv-frontend mythtv-theme-arclight
  mythtv-theme-childish mythtv-theme-graphite mythtv-theme-metallurgy mythtv-theme-mythbuntu
  mythtv-themes mythtv-transcode-utils mythvideo mythweather

---

### Post by tgm4883 on 2011-01-21
> **milesnorth said:**
> Hopefully this helps.

~$ sudo aptitude install mythtv-frontend -V

The following packages will be upgraded: 
  
  libmyth-0.24-0 [2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 -> 2:0.24.0+fixes.20110120.90fe13c-0ubuntu0mythbuntu2]  
  mythtv-frontend [2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 -> 2:0.24.0+fixes.20110120.90fe13c-0ubuntu0mythbuntu2]  
  
Likely not much help, but Apt-get upgrade shows these 21 packages:

The following packages will be upgraded:
  libmyth-0.24-0 libmyth-python libmythtv-perl mytharchive mythbrowser mythmusic mythnetvision mythtv
  mythtv-backend mythtv-common mythtv-database mythtv-frontend mythtv-theme-arclight
  mythtv-theme-childish mythtv-theme-graphite mythtv-theme-metallurgy mythtv-theme-mythbuntu
  mythtv-themes mythtv-transcode-utils mythvideo mythweather

2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 -> 2:0.24.0+fixes.20110120.90fe13c-0ubuntu0mythbuntu2

That's a legit upgrade. It's actually an upgrade from the Jan 6th build to the Jan 20th build. If you let it do the upgrade does it offer you upgrade right afterward?

---

