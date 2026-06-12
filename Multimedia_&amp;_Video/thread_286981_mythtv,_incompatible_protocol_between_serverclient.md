---
title: "mythtv, incompatible protocol between server/client in edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by supirman on 2006-10-28
I had mythtv running on dapper, and now that I've upgraded to edgy, it will no longer work.  I have proceeded to install/uninstall all mythtv packages numerous times to no avail.  I continually get this error when trying to watch live tv:
"The server uses protocol version 31, but this client only understands version 30.  Make sure you are running compatible versions of the backend and frontend."

From googling, it appears that perhaps the backend was taken from the -fixes branch in svn, where the protocol version was updated, but the frontend wasn't.  


When checking installed packages, they all seem ok: 
```

foerster@zeus:~$ dpkg -l|grep myth
ii  libmyth-0.20                           0.20-0.2ubuntu2                       Common library code for MythTV and add-on mo
ii  mythtv                                 0.20-0.2ubuntu2                       A personal video recorder application (clien
ii  mythtv-backend                         0.20-0.2ubuntu2                       A personal video recorder application (serve
ii  mythtv-common                          0.20-0.2ubuntu2                       A personal video recorder application (commo
ii  mythtv-database                        0.20-0.2ubuntu2                       A personal video recorder application (datab
ii  mythtv-frontend                        0.20-0.2ubuntu2                       A personal video recorder application (clien
ii  mythweb                                0.20-0.6ubuntu4                       Web interface add-on module for MythTV


```


Has anybody been able to get mythtv running on edgy? ](*,)

---

### Post by superm1 on 2006-10-30
Those packages are indeed the latest packages.  Are you trying to run both the backend and frontend on this box?  

Both the backend and frontend are built from this same source package which does use protocol 31 (which was provided from 0.20-fixes branch)

---

### Post by supirman on 2006-10-30
Yes, I'm trying to run the backend and the frontend on the same machine.  I don't know why I'm getting this issue, as I've uninstalled/reinstalled the packages multiple times.  dpkg says I'm using the latest packages.  Maybe there is some older version still laying around on the system.  I think I may do a fresh install of edgy as my current system is becoming quite cluttered.  I'll let you know how it goes after I reformat everything.

---

### Post by superm1 on 2006-10-30
If you think there is some old version laying around, look in /usr/local for any libmyth related files.  Wouldn't surprise me if you installed from source and had some things hanging out there.

---

### Post by supirman on 2006-10-30
As it turns out, I had installed .20 from source in dapper, and some of the libraries were still resident on my box.  I just wiped out all of the myth libraries with:

rm /usr/lib/libmyth* 

and reinstalled mythtv.  All is working well again.

Thanks!

---

### Post by superm1 on 2006-10-31
And this is why I don't condone spewing results of make install all over a box ;)

If you install packages from source, try to always checkinstall instead of make install.  It will keep things a bit cleaner.

---

### Post by supirman on 2006-10-31
I've never used checkinstall, but perhaps I should :D

---

### Post by dannyboy79 on 2006-10-31
hey there, can you tell me exactly what source files you used to install mythtv on your dapper box, I want the latest greatest. i also want my box to be a front and backend. i have a pvr-350. i heard that the version in the repo's is old. by reading your thread, it sounds like you're using the latest, where do I get ALL the stuff I need to do an install? Thanks ahead of time.

---

### Post by superm1 on 2006-10-31
> **dannyboy79 said:**
> hey there, can you tell me exactly what source files you used to install mythtv on your dapper box, I want the latest greatest. i also want my box to be a front and backend. i have a pvr-350. i heard that the version in the repo's is old. by reading your thread, it sounds like you're using the latest, where do I get ALL the stuff I need to do an install? Thanks ahead of time.

Dannyboy, I am hosting a repository that includes mythtv packages for dapper.

Edit your /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list

```
Add these to the bottom
```
         deb http://home.eng.iastate.edu/~superm1 dapper main
        deb-src http://home.eng.iastate.edu/~superm1 dapper main       
```

Add my GPG key that I sign the repo with:
```
wget http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -
```

I have ivtv included here, and the ivtv documentation at 
[https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)
will be very similar to how you would install ivtv.  The only big differences would be the exact naming of the packages to install are 
**ivtv0.4-source and ****ivtv0.4-utils ivtv-firmware**
I included the firmware on that repository though.

---

### Post by dannyboy79 on 2006-10-31
> **superm1 said:**
> Dannyboy, I am hosting a repository that includes mythtv packages for dapper.

Edit your /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list

```
Add these to the bottom
```
         deb http://home.eng.iastate.edu/~superm1 dapper main
        deb-src http://home.eng.iastate.edu/~superm1 dapper main       
```

Add my GPG key that I sign the repo with:
```
wget http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -
```

I have ivtv included here, and the ivtv documentation at 
[https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)
will be very similar to how you would install ivtv.  The only big differences would be the exact naming of the packages to install are 
**ivtv0.4-source and ****ivtv0.4-utils ivtv-firmware**
I included the firmware on that repository though.

superm1, you're the bomb. That is so cool that you made some .debs for all of us. Where are the exact instructions I would follow to perform a total front and backend usable desktop system. I saw that you wrote it up for Edgy but is it the same for Dapper? Again, thank you so much for this as learning to use Linux was mostly because I hated the way my ati all in wonder 9800 pro worked, the software that ran the tv was horrible, I couldn't do programing very easily etc etc. so hopefully mythtv will be better along with my pvr-350.

---

### Post by superm1 on 2006-10-31
Dannyboy,

Most of that writeup for Edgy should work for dapper.  I've been puting so much time towards edgy, that I haven't had much time to check everything for correctness in both.  If you can move up to edgy, it would be a much smoother process, and I can help you through exact problems a bit better.

If not, follow the edgy process, and check for correctness against dapper.  If you hit a hurdle somewhere for something that doesn't work in dapper, let me know & i'll put it into the dapper section.

---

### Post by dannyboy79 on 2006-11-01
> **superm1 said:**
> Dannyboy,

Most of that writeup for Edgy should work for dapper.  I've been puting so much time towards edgy, that I haven't had much time to check everything for correctness in both.  If you can move up to edgy, it would be a much smoother process, and I can help you through exact problems a bit better.

If not, follow the edgy process, and check for correctness against dapper.  If you hit a hurdle somewhere for something that doesn't work in dapper, let me know & i'll put it into the dapper section.


i don't want to move to edgy because everything is working great for me right now in Dapper plus, dapper has the long term support were as edgy doesn't (i don't think anyway). If someone could guarentee me that an upgrade would work or that if I did a frresh install and then restored my /home/ partition and all my installed software would be ok (samba, sbackup, proftpd, etc etc) then just maybe I would upgrade but I have read horror story after horror story about people trying to upgrade and then they break there system!

---

### Post by superm1 on 2006-11-01
> **dannyboy79 said:**
> i don't want to move to edgy because everything is working great for me right now in Dapper plus, dapper has the long term support were as edgy doesn't (i don't think anyway). If someone could guarentee me that an upgrade would work or that if I did a frresh install and then restored my /home/ partition and all my installed software would be ok (samba, sbackup, proftpd, etc etc) then just maybe I would upgrade but I have read horror story after horror story about people trying to upgrade and then they break there system!

I can see your reluctance to upgrade.  I myself had some breakage with a few things with the upgrade.  I've sorted all but one of them out.

I'm planning to keep a backend running dapper (for the same reasons, I don't really want to deal with any breakage), so I'll be building packages for dapper still.

Let me know if anything in the guide doesn't work or doesn't make sense for dapper :)

---

### Post by dannyboy79 on 2006-11-01
> **superm1 said:**
> I can see your reluctance to upgrade.  I myself had some breakage with a few things with the upgrade.  I've sorted all but one of them out.

I'm planning to keep a backend running dapper (for the same reasons, I don't really want to deal with any breakage), so I'll be building packages for dapper still.

Let me know if anything in the guide doesn't work or doesn't make sense for dapper :)

WAIT, when you say that you'll be building packages for dapper still does that mean that your current deb's don't work for dapper? I don't think that's what you meant but I am just curious as to what you mean by that statement. When I do the install using the edgy guide i'll let you know if there are any problems you can count on that (ha ha) because I'll most likely be pm'ing you for help if you don't mind that is.

---

### Post by superm1 on 2006-11-01
> **dannyboy79 said:**
> WAIT, when you say that you'll be building packages for dapper still does that mean that your current deb's don't work for dapper? I don't think that's what you meant but I am just curious as to what you mean by that statement. When I do the install using the edgy guide i'll let you know if there are any problems you can count on that (ha ha) because I'll most likely be pm'ing you for help if you don't mind that is.

You just misread.  My debs on home.eng.iastate.edu/~superm1 are built for dapper.  I have an edgy section there too, and will add a feisty section as the mythtv maintainer team moves along.

---

### Post by dlai on 2006-11-02
So I imagine some of you guys must have a card using the IVTV-drivers, and I was just curious as to how exactly you manage to make the tv-channels and the tv-information be in sync. Is there a way to tell a channel to apply to a certain channel in the xmltv information for example?

---

### Post by dannyboy79 on 2006-11-02
> **dlai said:**
> So I imagine some of you guys must have a card using the IVTV-drivers, and I was just curious as to how exactly you manage to make the tv-channels and the tv-information be in sync. Is there a way to tell a channel to apply to a certain channel in the xmltv information for example?

well I have a PVR-350 and I believe that it has the ivtv chipset or whatever but I am sorry to say that I haven't done the install yet. I can tell you that my goal is to set it up with an ir blaster so that my cable box controls the channels within mythtv. i am hoping that mythtv will be able to display my hbo channel because my main goal is to record Sopranos when it comes back on, Deadwood, etc, etc. I know that when I hooked my cable line directly to my AIW 9800 pro on my winbloz box it only got certain stations and I never looked into getting it to be able display premium stations.  Sorry to get so far off topic, your question sounds easy enough to solve for the guy that wrote the deb's for us. The guy with the mario pic.

---

### Post by superm1 on 2006-11-03
> **dlai said:**
> So I imagine some of you guys must have a card using the IVTV-drivers, and I was just curious as to how exactly you manage to make the tv-channels and the tv-information be in sync. Is there a way to tell a channel to apply to a certain channel in the xmltv information for example?
Well are you using zap2it (eg USA,canada)?  Or are you for sure stuck using xmltv?

---

### Post by dannyboy79 on 2006-11-03
> **superm1 said:**
> Well are you using zap2it (eg USA,canada)?  Or are you for sure stuck using xmltv?

SUPERM1, are you aware if i my mythtv box will be able to display ever single channel gets displayed thru my cable box? because like I was saying, if I hook the cable right to the pvr-350 I onl get certain channels,(no premium etc etc) so if I first plug into my cbale box, and then from that into the mythtv box, will this allow me to be able to record and show all the normal channels that the cable box displays? then from what I read, I will need to install a ir blaster so that when I change the channel on the cable box, it changes on the mythtv also, or vice versa I think? does all this sound possible?

---

### Post by superm1 on 2006-11-03
> **dannyboy79 said:**
> SUPERM1, are you aware if i my mythtv box will be able to display ever single channel gets displayed thru my cable box? because like I was saying, if I hook the cable right to the pvr-350 I onl get certain channels,(no premium etc etc) so if I first plug into my cbale box, and then from that into the mythtv box, will this allow me to be able to record and show all the normal channels that the cable box displays? then from what I read, I will need to install a ir blaster so that when I change the channel on the cable box, it changes on the mythtv also, or vice versa I think? does all this sound possible?

This sounds right, you can't get premium without a cable box.  With the cable box you will be able to get all of the channels - but you will need a method to change channels on the box.  This can be a serial channel changer, firewire channel changer, or ir blaster.

I personally work off of a firewire channel changer - its always been very reliable.

Find out what your cable company offers, if you can get a box with firewire - you can possibly do TV captures through firewire as well as change channels.  If you can get a serial, you will need a straight thru serial cable to change channel with.

---

### Post by dlai on 2006-11-04
> **superm1 said:**
> Well are you using zap2it (eg USA,canada)?  Or are you for sure stuck using xmltv?

Well I live in Denmark and I think xmltv is the only possibility!

---

### Post by superm1 on 2006-11-04
> **dlai said:**
> Well I live in Denmark and I think xmltv is the only possibility!

Well this being the case, i'm sorry but I can't offer any assistance with xmltv as i've never worked with it (i'm usa with zap2it).  Checkout the myth docs, wiki, mailing list for more info about how xmltv works.

---

