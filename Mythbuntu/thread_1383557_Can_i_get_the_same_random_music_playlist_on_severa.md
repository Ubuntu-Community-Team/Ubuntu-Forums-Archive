---
title: "Can i get the same random music playlist on several frontends?"
date: 2010-01-17
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-01-17
Hi guys,

i have a myth box in my living room and am looking to put another frontend in my kitchen.  I would like to have the same music playing on both front ends, even if i choose random within mythmusic (ie if i have a party the music is the same in both rooms). 

Is this easy to do?  Or can it be done?  

Thanks

---

### Post by geekyhawkes on 2010-01-18
Anyone?

---

### Post by kja999 on 2010-01-19
+1 for me on this .. I'de be interested in it as a feature, but don't think Myth does this yet ...

---

### Post by matt06 on 2010-01-19
I just tried doing this via the MythMusic interface in Mythweb and it worked great.  On my system the page is at [http://mythtv/mythweb/music](http://mythtv/mythweb/music)  Just add the files you want (or random) to a playlist and save it.  It should now show up as a playlist selection in MythMusic on your frontend.

EDIT:  Oops, I see that the OP really wants "synced" music output on both frontends, not just the same playlist.

---

### Post by nickrout on 2010-01-19
If you want sync'd music I suggest getting squeezebox server and installing mythsqueezebox2 on each frontend.

---

### Post by geekyhawkes on 2010-01-20
i actually have a squeezebox upstairs in my house as well.  Could you talk me through quickly how i would use the squeeze server to sync music across the 2 myth machines? 

I only have the slimserver (or what ever they are calling it this week) installed on my backend at the moment.

I have seen the youtube for mythsqueezebox2 but it didnt mention any ability to sync several clients/squeezeboxes to the same playlist.

Is there an install guide anywhere for mythsqueezebox2?

---

### Post by nickrout on 2010-01-20
> **geekyhawkes said:**
> i actually have a squeezebox upstairs in my house as well.  Could you talk me through quickly how i would use the squeeze server to sync music across the 2 myth machines? 

I only have the slimserver (or what ever they are calling it this week) installed on my backend at the moment.

I have seen the youtube for mythsqueezebox2 but it didnt mention any ability to sync several clients/squeezeboxes to the same playlist.

Is there an install guide anywhere for mythsqueezebox2?

search the mailing list archives for mythsqueezebox2, the install instructions are there.

once you have two squeezebox clients they are easy to synchronise, on the device go to settings|synch with|

or it can be done on the web interface.

---

### Post by geekyhawkes on 2010-01-23
I have looked here 

[http://www.gossamer-threads.com/lists/mythtv/users/404250](http://www.gossamer-threads.com/lists/mythtv/users/404250)

but am having problems understanding what i need to do to get it installed.  I have installed everything terminal suggests to get svn working and tried 

sudo svn co
[https://mythsqueezebox.svn.sourceforge.net/svnroot/mythsqueezebox/mythsqueezebox2](https://mythsqueezebox.svn.sourceforge.net/svnroot/mythsqueezebox/mythsqueezebox2)

but i keep getting

svn: OPTIONS of 'https://mythsqueezebox.snv.sourceforge.net/svnroot/mythsqueezebox/mythsqueezebox2': could not connect to server ([https://mythsqueezebox.snv.sourceforge.net](https://mythsqueezebox.snv.sourceforge.net))


back.  I can navigate through firefox to that web location so am confused what i am doing wrong!

---

### Post by nickrout on 2010-01-23
> **geekyhawkes said:**
> I have looked here 

[http://www.gossamer-threads.com/lists/mythtv/users/404250](http://www.gossamer-threads.com/lists/mythtv/users/404250)

but am having problems understanding what i need to do to get it installed.  I have installed everything terminal suggests to get svn working and tried 

sudo svn co
[https://mythsqueezebox.svn.sourceforge.net/svnroot/mythsqueezebox/mythsqueezebox2](https://mythsqueezebox.svn.sourceforge.net/svnroot/mythsqueezebox/mythsqueezebox2)

but i keep getting

svn: OPTIONS of 'https://mythsqueezebox.snv.sourceforge.net/svnroot/mythsqueezebox/mythsqueezebox2': could not connect to server ([https://mythsqueezebox.snv.sourceforge.net](https://mythsqueezebox.snv.sourceforge.net))


back.  I can navigate through firefox to that web location so am confused what i am doing wrong!

You seem to have mistyped the url. It should be svn not snv.

---

### Post by geekyhawkes on 2010-01-24
Right now im typing the new url i have gotten a bit further, but still having problems with the install / prereqs.  The readme states the following as required;


libportaudio	available through [http://www.portaudio.com](http://www.portaudio.com).  Need version >- .19
libFLAC		
libmad 
libogg 
libvorbisfile 
libvorbis 
curses (NOTE: this is to build squeezeslave, which needs it to provide an interface that we piggyback off of).


I have downloaded and untar'd the latest version of portaudio but do i need to make and make install it?  Also where do i find the rest of the reqs?  I have tried sudo apt-get install for each of them but they are not known by my system. 

Also, i tried a make without them and had pages of errors so not that keen to press on with a make install.

---

### Post by geekyhawkes on 2010-02-01
Can anyone help me with the above issues?  THanks

---

### Post by nickrout on 2010-02-01
> **geekyhawkes said:**
> Right now im typing the new url i have gotten a bit further, but still having problems with the install / prereqs.  The readme states the following as required;


libportaudio	available through [http://www.portaudio.com](http://www.portaudio.com).  Need version >- .19
libFLAC		
libmad 
libogg 
libvorbisfile 
libvorbis 
curses (NOTE: this is to build squeezeslave, which needs it to provide an interface that we piggyback off of).


I have downloaded and untar'd the latest version of portaudio but do i need to make and make install it?  Also where do i find the rest of the reqs?  I have tried sudo apt-get install for each of them but they are not known by my system. 

Also, i tried a make without them and had pages of errors so not that keen to press on with a make install.

```
sudo aptitude install libportaudio2 libogg0 libvorbis0 libflac8 libmad0
```

although most are probably installed already!

---

### Post by geekyhawkes on 2010-02-01
Thanks, any idea why the make is failing then if i have them installed already?

---

### Post by nickrout on 2010-02-01
> **geekyhawkes said:**
> Thanks, any idea why the make is failing then if i have them installed already?

fails for me too. may pay to email the author, his email address is in that archive thread you pointed to.

---

