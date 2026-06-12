---
title: "Unknown channel 'karmic-partner'"
date: 2009-12-30
forum: Mythbuntu
---

### Post by jerryk1234 on 2009-12-30
Hello,

    I just downloaded Mythbuntu.... I'd like to use it on an ITX pc that I bought for the TV.  Mainly, I'd like to be able to watch Internet videos, such as on Hulu, youtube, etc.   Have no interest in watching live TV on it at this time,  the TV set itself has a perfectly good ATSC tuner.

   A logical first step seems to be to get an adobe FLash player working.  

Going to the Adobe web site, I found their download page, and  clicked to install the latest stable release.
I chose "APT for Ubuntu 9.04+".  Firefox wanted me to choose an installer program, I guessed
"/usr/bin/apturl".

A message box appeared:  "Unknown channel 'karmic-partner'
                                        "The channel 'karmic-partner' is not known"


Anybody have a clue?  There are four files in /usr/bin with the string "Unknown channel":
tv_grab_hr, tv_grab_no_gfeed, tv_grab_se_swedb.  They all seem to be perl scripts having to do with getting program listings.  For live tv?

As I said, I really have no interest ( at this time ) in live TV.  Any way to bypass this error?  Google
was no help.

Thanks in advance,

                                  - Jerry Kaidor

---

### Post by jerryk1234 on 2009-12-30
OK, I got around that one.  I believe that the "unknown channel" had to do with Ubuntu's method of getting packages.

Eschewing the magic of automated installation, I just got the tar.gz from Adobe.  Whups, the current stable version tar.gz doesn't have the installer.  It only has the shared library.   So I went to Adobe's "bleeding edge Beta" page and downloaded that one.

It was downhill from there on.  The only even remotely challenging thing was when the installer asked for the "browser installation directory".  Whazzat?  OK, I said "find / -name firefox" and found /usr/lib/firefox-3.5.3 with a bunch of stuff in it.  Specified that, and the install was finished in a couple of seconds.

In my tiredness and frustration last night, I neglected to introduce myself.  

My name is Jerry Kaidor, and I'm actually a fairly experienced Linux-er.  I've been using and playing with Linux since about
1992, starting with kernel version 0.95.   
 These days, I maintain a couple of servers with Perl/CGI/mysql/etc  scripts for running my business.   I have no experience with Ubuntu - have used Slackware these many years - and before that, SLS, and before that the 
"MCC Interim Distribution", which was a pile of about 15 floppies.

I keep all important data on my linux machines.  My motto: "Don't put anything on a Windows box that you can't buy at the store" :).

                 - Jerry Kaidor

---

