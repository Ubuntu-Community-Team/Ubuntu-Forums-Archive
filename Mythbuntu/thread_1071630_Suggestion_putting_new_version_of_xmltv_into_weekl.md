---
title: "Suggestion: putting new version of xmltv into weekly builds"
date: 2009-02-16
forum: Mythbuntu
---

### Post by scottishnarn on 2009-02-16
I hope this is the right place for this, if not please tell me. 

I currently use Mythbuntu 8.04. As every previous upgrade of my mythtv software has taken a few weeks to get the bugs out of the system (I usually dual boot until I'm satisfied I've got everything running smoothly) I don't want to have to upgrade every 6 months. 

However, I get my tv listings from the radiotimes (I need sky channels as well as freeview) using xmltv. A couple of weeks ago it stopped updating, the radiotimes had changed the format of the xml data or channel names or something, anyway it broke. I fixed it by manually installing the latest version of xmltv from the website. But I had to fiddle around a bit to get it working. I had to do this with my last mythtv system as well (which I had running for around 18months before upgrading to 8.04).

If was just wondering if it might be useful to put updates to xmltv into either the mythbuntu repositories or the weekly builds one. If I didn't know what I was doing with linux I would have been stuck with a useless system, as mythtv is not much use without listings. I'm sure this would help people with less experience and is my opinion pretty much essential if you want mythbuntu to be regarded in any sense as LTS.

---

### Post by Steve Goodey on 2009-02-18
Seconded.

Steve.

---

### Post by scottishnarn on 2009-02-18
Just in case anyone is interested in what I had to do to get it working. 

Download the latest version of xmltv from [http://wiki.xmltv.org/index.php/Main_Page](http://wiki.xmltv.org/index.php/Main_Page)

Run the following commands
```
perl Makefile.PL PREFIX=/opt/xmltv
make
sudo make install
sudo mv /usr/bin/tv_grab_uk_rt /usr/bin/tv_grab_uk_rt_old
sudo ln -s /opt/xmltv/bin/tv_grab_uk_rt /usr/bin
```This installs to /opt/xmltv 
I use uk radio times listings hence I modify tv_grab_uk_rt
I copy the old file and link my installed version to /usr/bin

I do it this way so that if there is an updated version available via apt-get at some point I can delete the link, rename the file back and update as normal. 

I tried removing the apt-get version and just installing the new version (again in /opt/xmltv with a link to /usr/bin to make it easy to remove) but it didn't work. Not sure why, so I just left it in place.

Hope this helps someone else.
David

---

