---
title: "Quick guide to install pulseaudio-equalizer in maverick"
date: 2010-09-14
forum: Multimedia Software
---

### Post by shantiq on 2010-09-14
[**for most recent and fastest **way to install read here=====>]("http://ubuntuforums.org/showpost.php?p=9919120&postcount=7")

============================================================

---

### Post by eimhin85 on 2010-09-14
Hiya

after renaming the software sources i get:-

E: Malformed line 2 in source list /etc/apt/sources.list.d/psyke83-ppa-maverick.list (dist parse)

---

### Post by Lawrence Talbot on 2010-09-14
One equalizer for the whole system would be good.  Thanks.:D

---

### Post by shantiq on 2010-09-15
> **eimhin85 said:**
> Hiya

after renaming the software sources i get:-

E: Malformed line 2 in source list /etc/apt/sources.list.d/psyke83-ppa-maverick.list (dist parse)



look it says pp-maverick.list  on your line you have skipped  stage **2.** it seems where you change maverick to lucid

this

[COLOR="DarkRed"]At this stage you need to go system/admin/software sources and change maverick to lucid in the repository since it does not exist as yet for maverick


Highlight both psyke83 lines click on edit and change maverick for lucid then reload[/COLOR]



try that again then it should go through.


shan

---

### Post by eimhin85 on 2010-09-15
> **shantiq said:**
> look it says pp-maverick.list  on your line you have skipped  stage **2.** it seems where you change maverick to lucid

this

[COLOR=DarkRed]At this stage you need to go system/admin/software sources and change maverick to lucid in the repository since it does not exist as yet for maverick


Highlight both psyke83 lines click on edit and change maverick for lucid then reload[/COLOR]



try that again then it should go through.


shan

I have not skipped stage 2 lol. I know that its weird. I dont know why. 
I even did:

gedit /etc/apt/sources.list.d/psyke83-ppa-maverick.list

and the contents are correct:-

deb [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) lucid main

After that, i renamed them  anyway

sudo mv psyke83-ppa-maverick.list.save psyke83-ppa-lucid.list.save
sudo mv psyke83-ppa-maverick.list psyke83-ppa-lucid.list

but still nothing

---

### Post by shantiq on 2010-09-15
sorry eimhin we need someone with more knowledge than myself to help you here with this i do not understand where the word maverick  came from since the ppa is lucid      

 shan

---

### Post by shantiq on 2010-10-03
there now is a [.deb]("https://launchpad.net/~nilarimogard/+archive/test/+files/pulseaudio-equalizer_2.7.0.1-1_all.deb") and also  ppa designed specifically for maverick with all corrections included


first saw it mentioned[URL="http://ubuntuforums.org/showpost.php?p=9916014&postcount=293"] here
[/URL]


```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update && sudo apt-get install pulseaudio-equalizer
```


deb also attached here




===========================================================

and if you wanted to remove totally

```
sudo apt-get remove && sudo apt-get purge pulseaudio-equalizer-gtk  ladspa-sdk
```

---

### Post by Valis667 on 2010-11-06
**[SIZE="7"]*******WARNING*******[/SIZE]**

[SIZE="5"]Do NOT install this software, it will mess up your sound completely![/SIZE]

---

### Post by shantiq on 2010-11-06
valis that may not be a very useful intervention

if you have had problems on your system maybe explain what they are


many others are very happy with pulseaudio-equalizer

there may be a clash between your system and this particular software

so what happened if you do not mind sharing?

---

### Post by Elwood72 on 2010-11-14
> **shantiq said:**
> valis that may not be a very useful intervention

if you have had problems on your system maybe explain what they are


many others are very happy with pulseaudio-equalizer

there may be a clash between your system and this particular software

**so what happened if you do not mind sharing?**

I know this wasn't directed at me,but I tried the same thing,and got this:

> W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Some background:

I just did the update to 10.10 this morning. I did the so-called "Dirty" update. I was having a few issues and thought that an update would chase them out,and it did,for the most part. I now have sound (back),but I can't get the EQ back. 


When the update first started,I was notified via a pop-up that I would need to re-install some packages manually.....unfortunately,I didn't make note of what they were.....

....which probably explains my dilemma.

Still no EQ....


I'm also having issues with the screensaver,but I'll find the proper threads for that.....

---

### Post by shantiq on 2010-11-14
elwood


maybe read [this part ]("http://ubuntuforums.org/showpost.php?p=9919120&postcount=7")of the post again


the earlier links you mention are now broken


good luck with the new ones  i would suggest the .deb file as it is straighforward   


 shan

---

### Post by Elwood72 on 2010-11-14
> **shantiq said:**
> elwood


maybe read [this part ]("http://ubuntuforums.org/showpost.php?p=9919120&postcount=7")of the post again


the earlier links you mention are now broken


good luck with the new ones  i would suggest the .deb file as it is straighforward   


 shan

Thanks....

I didn't miss it the first time around,but I *did* run through the steps again,just to be sure.

I also went to the Package Manager,and marked the pertinent package for an upgrade.That was the fix,so I now have am EQ.

Thanks again for the quick reply...


...on to the screensaver issue (in the proper area.:P )

---

