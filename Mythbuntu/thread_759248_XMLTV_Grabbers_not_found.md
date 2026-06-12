---
title: "XMLTV Grabbers not found"
date: 2008-04-18
forum: Mythbuntu
---

### Post by ayster on 2008-04-18
Hi,
Just installed Mythbunto 8.04 RC. When I try and set up my video sources, the only XMLTV grabber showing is north america, I can only see this, direct epg or no grabber, yet I can manually run tv_grab_uk_rt with no problems... so how do I make it show up in MythTV Setip?

cheers.
Ayster

---

### Post by ayster on 2008-04-19
As nobody's replied to this yet, I've done a work around, I created a shell script that runs tv_grab_uk_rt and outputs to a file called xmltvuk.xmltv, then it runs mythfilldatabase --file 1 xmltvuk.xmltv to import that into the database, seems to work ok, but really would like a proper solution (i.e. having XMLTV on the sources page!)

cheers

---

### Post by laga on 2008-04-19
When you run mythtv-setup in a terminal, does it say "Running tv_find_grabbers." in the terminal window? Do you get a progress bar telling you that it's looking for XMLTV grabbers? What does 'tv_find_grabbers' return?

---

### Post by cchi on 2008-05-16
I am having exactly the same problem here in Japan...
Ubuntu 8.04 with latest MythTV from Ubuntu packages.
- The Video Sources page spends time looking for grabbers (presumably running tv_find_grabbers).
- I can manually run tv_find_grabbers, and get /usr/bin/tv_grab_jp|Japan as one of the lines of output.
- I can also run tv_grab_jp, and it churns our a list of TV shows in XML..

....BUT, I cant see tv_grab_jp in the Video Sources page of MythTV.  I only get the standard "North America (SchedulesDirect.org)" one...

I don't know how to use your workaround above, and am desperate!  Please help.

---

### Post by SteveGodfrey on 2008-05-18
I have the same problem. I want to run uk_rt but it isn't listed in the video sources page.

Any ideas what's causing this?

---

### Post by robho on 2008-05-18
I ran into this problem too, but found a quick solution.

My problem was that "tv_find_grabbers" takes more than 25 seconds to complete. If that happens mythtv-setup will not get a list of the available grabbers.

I removed some of the /usr/bin/tv_grab_* grabbers which I wasn't using and after that tv_find_grabbers could complete within 25 seconds.

This has been reported as [mythtv bug 5375]("http://svn.mythtv.org/trac/ticket/5375")

---

### Post by cchi on 2008-05-18
> **robho said:**
> I ran into this problem too, but found a quick solution.

My problem was that "tv_find_grabbers" takes more than 25 seconds to complete. If that happens mythtv-setup will not get a list of the available grabbers.

I removed some of the /usr/bin/tv_grab_* grabbers which I wasn't using and after that tv_find_grabbers could complete within 25 seconds.

This has been reported as [mythtv bug 5375]("http://svn.mythtv.org/trac/ticket/5375")

Great!  Ill try that, thanks for letting us know.

---

### Post by fdkuyper on 2008-05-22
> **laga said:**
> When you run mythtv-setup in a terminal, does it say "Running tv_find_grabbers." in the terminal window? Do you get a progress bar telling you that it's looking for XMLTV grabbers? What does 'tv_find_grabbers' return?

For me this gave the solution: when I tried this, I got:

The program 'tv_find_grabbers' is currently not installed.  You can install it by typing:
sudo apt-get install xmltv-util

After installing xmltv-util it worked for me! :)

Thanks!

---

### Post by gunrock on 2008-08-13
> **robho said:**
> I ran into this problem too, but found a quick solution.

My problem was that "tv_find_grabbers" takes more than 25 seconds to complete. If that happens mythtv-setup will not get a list of the available grabbers.

I removed some of the /usr/bin/tv_grab_* grabbers which I wasn't using and after that tv_find_grabbers could complete within 25 seconds.

This has been reported as [mythtv bug 5375]("http://svn.mythtv.org/trac/ticket/5375")

Thanks for that. Due to my exceptionally slow hardware (Via C3 1gz) this was taking longer than 25 secs and failing in the same way. Removing all the grabbers except the one I wanted, fixes the issue for me.

---

### Post by nickrout on 2008-08-13
I think the solution is to install the xmltv package:```
sudo aptitude install xmltv
```

Then they will appear in mythsetup.

---

### Post by gunrock on 2008-08-14
> **nickrout said:**
> I think the solution is to install the xmltv package:```
sudo aptitude install xmltv
```

Then they will appear in mythsetup.

I did that and still it didn't work. So I tried the other suggestion whci hworked for me (my mythfilldatabase works and I have the UK Radio Times listings in there, as desired).

---

### Post by moorsey on 2008-11-06
ahh, excellent, glad there are others with this issue.  I am trying to delete some of these files, but do not have access to do so, which seems to be happening quite a lot with various commands, guess I'm going wrong somewhere?

edit, figured it out, just stick "sudo" in front of it, thanks guys!

---

