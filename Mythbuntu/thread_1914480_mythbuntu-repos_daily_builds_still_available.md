---
title: "mythbuntu-repos daily builds still available?"
date: 2012-01-24
forum: Mythbuntu
---

### Post by soho on 2012-01-24
Hi,

Recently most national dvb-t channels changed audio protocol after which audio is chunky in mythtv and the log is flooded with error messages.

According to the mythtv issue tracker this problem (a feature in ffmpeg that was disabled) has been fixed a while ago in the source trunk.

The problem is that I don't get the daily build updates anymore.
I have installed and reinstalled the mythbuntu-repos package from [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos), but there is no mythtv updates available in the update manager.

So my questions are: Is the daily builds still maintained as a ubuntu package?
If so, how do I enable those?
If not, is there a relatively easy way to update mythtv (and ffmpeg) to a new version?

---

### Post by nickrout on 2012-01-24
> **soho said:**
> Hi,

Recently most national dvb-t channels changed audio protocol after which audio is chunky in mythtv and the log is flooded with error messages.

According to the mythtv issue tracker this problem (a feature in ffmpeg that was disabled) has been fixed a while ago in the source trunk.

The problem is that I don't get the daily build updates anymore.
I have installed and reinstalled the mythbuntu-repos package from [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos), but there is no mythtv updates available in the update manager.

So my questions are: Is the daily builds still maintained as a ubuntu package?
If so, how do I enable those?
If not, is there a relatively easy way to update mythtv (and ffmpeg) to a new version?

when exactly was your problem fixed?

they have not been "daily" for some time, they are built when there is a change.

You basically have two options:

0.24-fixes - the latest 0.24 sources with fixes applied to the 0.24 branch since 0.24 was released. This is best for day to day use.

0.25 - which is "master" - formerly "trunk" - experimental code which may or may not work on anay prticular day. Tio run this you should subscribe to mythtv-dev and -commits mailing lists and be prepared to test code, and to expect breakage from time to time.

---

### Post by joshoekstra on 2012-01-25
Is there any info on building problems? Today I see a mix of packages for trunk with datestamps 20120122 and 20120125, synaptic and updatemanager will let me update, but experience has tought me to never mix n match with packages.
The packages seem to have been build according to: 
[http://smithers.mythbuntu.org/~autobuild/weekly_mythtv.txt](http://smithers.mythbuntu.org/~autobuild/weekly_mythtv.txt)
The corresponding packages are not all there however...
It seems not al debs where uploaded at the time of writing.
Status can be checked by clicking on [this page]("https://launchpad.net/~mythbuntu") and selecting the package(.23, .24 and so on) and after that the packages-details. lucid-packages ending with 1, natty being 2 and up for more recent releases.

---

### Post by nickrout on 2012-01-25
Not sure, I am on 0.24-fixes.

---

### Post by soho on 2012-01-25
> **nickrout said:**
> when exactly was your problem fixed?


Actually I am not sure that the problem is fixed in the trunk at all. 
The symptoms are chunky audio when I view recordings.
The log error message is very generic:


```
2012-01-25 19:59:10.961 AFD: Opened codec 0x49f1550, id(AAC/LATM) type(Audio)
...
2012-01-25 19:59:11.547 AFD Error: Unknown audio decoding error
2012-01-25 19:59:11.919 AFD Error: Unknown audio decoding error
...repeated...

```

Playing thesame  recordings on the same machine using VLC works perfectly.

What I found in the Mythtv issue tracker was that the LATM driver had been disabled in some versions of Mythtv, and later inserted again. However, if LATM has been unavailable I assume I wouldn't hear anything, but I do hear chunky audio.

I did hope that I could find Mythbuntu 0.24-fixes easy-to-install binaries like previous, but apparently not so.

---

### Post by nickrout on 2012-01-25
> **soho said:**
> 

I did hope that I could find Mythbuntu 0.24-fixes easy-to-install binaries like previous, but apparently not so.

Make up your mind, do you want 0.24-fixes or do you want master (it is not trunk it is master since the move to git)

0.24 is presently at 0.24.2+fixes.20120124.e4660d6 for all my packages (on lucid). This is via mythbuntu repos. The binaries have never given me any problems.

---

### Post by superm1 on 2012-01-27
soho:

Now if you are testing "-master" builds you should realize that you can't go back to "-fixes" builds just by switching PPAs.  The version number of "-master" builds is higher than that of "-fixes" builds.  So you'll need to manually choose the version of the packages to install using a tool like synaptic or apt-get or remove all the mythtv packages and reinstall to let it select the lower version number when that PPA is in your sources.list

---

### Post by nickrout on 2012-01-27
> **superm1 said:**
> soho:

Now if you are testing "-master" builds you should realize that you can't go back to "-fixes" builds just by switching PPAs.  The version number of "-master" builds is higher than that of "-fixes" builds.  So you'll need to manually choose the version of the packages to install using a tool like synaptic or apt-get or remove all the mythtv packages and reinstall to let it select the lower version number when that PPA is in your sources.list

What's more your database is likely to be upgraded to be compatible with master and won't allow you to go back to 0.24.

---

### Post by superm1 on 2012-01-27
> **nickrout said:**
> What's more your database is likely to be upgraded to be compatible with master and won't allow you to go back to 0.24.

Oh very true.  My mention about reverting to 0.24 packages should be ignored if you are already on master.  You'll need to remove them and drop the mythconverg database from mysql for it to work properly.

---

