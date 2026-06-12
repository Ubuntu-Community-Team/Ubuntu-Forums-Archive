---
title: "wget Download Problem"
date: 2010-07-15
forum: Mythbuntu
---

### Post by Barry_IA on 2010-07-15
Hopefully this will keep someone else from having a several-weeks-long headache! <g>

Problem: the command "wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip"
results in an error message: "resolving [www.steventoth]("http://www.steventoth") net | 1.0.0.0 |:80 ... failed: Connection timed out. Retrying"  (Attempting to get the HVR-2250 drivers.)

Solved (here, anyway!):  Add the '-c' switch ==> "wget -c http://....."

The '-c' switch is for "continue".  Maybe at one time the download started and got interrupted, causing an incomplete file to be received.  Whatever the problem is the addition of the -c switch solved the problem for me and I can finally was able to get the drivers downloaded and installed.

---

### Post by goobie_7 on 2010-08-03
Thanks Barry_IA, saved a newbie ubuntu user from a headache.

Curiously though, from what I've read **wget "http://www.google.com"** should start downloading something (many sites use that as a test to see if you can use wget properly), however I get the error message you had above for that even if i throw in the -c switch, have I been lead astray?

---

### Post by Barry_IA on 2010-08-06
> **goobie_7 said:**
> Thanks Barry_IA, saved a newbie ubuntu user from a headache.

Curiously though, from what I've read **wget "http://www.google.com"** should start downloading something (many sites use that as a test to see if you can use wget properly), however I get the error message you had above for that even if i throw in the -c switch, have I been lead astray?

Hi Goobie_7, or rather G'Day! <g>

Unfortunately no idea.  I'm very new to Ubuntu/Linux and pretty much cook-booking the troubleshooting.  As I understand it, the *wget* command is for obtaining files, so it would not work with going to the Google site (should be able to use Firefox; if Firefox doesn't connect see the thread on deselecting IPv6 -- I submitted a reply to another user about a month ago on how to do that).

The *wget*  (or  *wget -c*) command would be used when obtaining a file from a site, so the format is something like site/directory/filename.

Hope that's helpful.

---

