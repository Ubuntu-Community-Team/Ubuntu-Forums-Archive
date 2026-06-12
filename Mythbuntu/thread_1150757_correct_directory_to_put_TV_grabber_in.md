---
title: "correct directory to put TV grabber in"
date: 2009-05-06
forum: Mythbuntu
---

### Post by Aijse on 2009-05-06
Hi,
I m trying to get a grabber I compiled to show up in the videosource section from the mythtv setup. Can someone tell what the correct directory is? I got it in /usr/bin now but it won't show up in the setup screen :S

Thanks in advance

---

### Post by ian dobson on 2009-05-06
Hi,

If linux doesn't already load the driver on starting, you just need to do an insmod modulename (to insert the module into the kernel).

Usually a driver/module will load automaticaly on boot if required. If it doesn't you can add it to your /etc/modules file.

Regards
Ian Dobson.

ps Abit more information about what hardware/driver your trying to get working with linux would help, as well as a link to the download page for the source/how to.

---

### Post by nickrout on 2009-05-06
umm I think he is referring to an xmltv grabber.

The command's name should I think be in the form tv_grab_* - see [http://packages.ubuntu.com/jaunty/all/xmltv-util/filelist](http://packages.ubuntu.com/jaunty/all/xmltv-util/filelist)

/usr/bin or /usr/local/bin are fine.

the command usr/bin/tv_find_grabbers finds all grabbers in the system. You might like to look at that script and see if it finds your grabber. It will also give you a clue as to what the format of the grabber script names is (ie how it identifies a tv grabber from other stuff in /usr/bin)

A related point is that mythtv-setup ues that usr/bin/tv_find_grabbers to locate grabbers. If it takes too long it times out and finds nothing. This can happen because recent versions of xmltv have a lot more grabbers than before and mythtv-setup doesn't allow enough time to find them all. A brute force but quick fix is to delete the grabbers you will never need.

ADDENDUM: I'm no perl expert but it looks to me like tv_find_grabbers looks for commands with the filename tv_grab_* then runs each command with the  --capabilities switch. If that fails I think it ignores the command. If it passes it runs the command with the --description switch to get a description which it uses in its output.

So at least 3 tests there:

is your script named right?

does it respond properly to the --capabilities switch?

does it respond properly to the --description switch?

---

### Post by Aijse on 2009-05-06
> **nickrout said:**
> umm I think he is referring to an xmltv grabber.

The command's name should I think be in the form tv_grab_* - see [http://packages.ubuntu.com/jaunty/all/xmltv-util/filelist](http://packages.ubuntu.com/jaunty/all/xmltv-util/filelist)

/usr/bin or /usr/local/bin are fine.

the command usr/bin/tv_find_grabbers finds all grabbers in the system. You might like to look at that script and see if it finds your grabber. It will also give you a clue as to what the format of the grabber script names is (ie how it identifies a tv grabber from other stuff in /usr/bin)

A related point is that mythtv-setup ues that usr/bin/tv_find_grabbers to locate grabbers. If it takes too long it times out and finds nothing. This can happen because recent versions of xmltv have a lot more grabbers than before and mythtv-setup doesn't allow enough time to find them all. A brute force but quick fix is to delete the grabbers you will never need.

ADDENDUM: I'm no perl expert but it looks to me like tv_find_grabbers looks for commands with the filename tv_grab_* then runs each command with the  --capabilities switch. If that fails I think it ignores the command. If it passes it runs the command with the --description switch to get a description which it uses in its output.

So at least 3 tests there:

is your script named right?

does it respond properly to the --capabilities switch?

does it respond properly to the --description switch?

Thanks Nickrout!

apparently I did not have all the xmltv packages corect. The tv_find_grabbers was not present. After I picked up the right packages it showed up and worked correctly :P

Thanks alot and good night

---

### Post by nickrout on 2009-05-06
> **Aijse said:**
> Thanks Nickrout!

apparently I did not have all the xmltv packages corect.Tthe tv_find_grabbers was not present. I picked up the right packages and it showed up. :P

Thanks alot and good night

and good morning from me!

Actually it seems weird that mythbuntu does not install xmltv by default. I suppose the north americans are happy with schedules direct and thats enough for the devs.

I think it is an option somewhere in mythbuntu's installation procedure, but I missed it the first time too :)

---

