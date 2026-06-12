---
title: "Do ISO's really work with storage groups in .24?"
date: 2010-10-01
forum: Mythbuntu
---

### Post by Slacker3k on 2010-10-01
I've been running 0.24 trunk for a while now with the hopes of using storage groups with ISO images.  According to the current release notes it's in, and looking at the patch - it's been in for a while.

But it still doesn't work for me...  it seems to be looking at the correct path at first, but then fails.

Does anyone have this working in 0.24 trunk?  Any more info?

Thanks.

---

### Post by iamlindoro on 2010-10-01
> **Slacker3k said:**
> 
Does anyone have this working in 0.24 trunk?  Any more info?


Works fine for me.  But sounds like you are trying to play back encrypted DVDs.  Myth supports ISOs via Storage Group just fine in trunk-- but libdvdcss (which is not a part of myth) has no knowledge of Myth's protocol.  If your ISOs are all still encrypted, then then won't work via storage group.  If you decrypt the content while you rip it, it'll play fine.

---

### Post by williammanda on 2010-10-01
> **iamlindoro said:**
> Works fine for me.  But sounds like you are trying to play back encrypted DVDs.  Myth supports ISOs via Storage Group just fine in trunk-- but libdvdcss (which is not a part of myth) has no knowledge of Myth's protocol.  If your ISOs are all still encrypted, then then won't work via storage group.  If you decrypt the content while you rip it, it'll play fine.

So does the decryption happen during the rip in mythtv when creating the ISO?

---

### Post by iamlindoro on 2010-10-01
> **williammanda said:**
> So does the decryption happen during the rip in mythtv when creating the ISO?

No.

---

### Post by Slacker3k on 2010-10-01
I wish it were that easy.  They are definitely not encrypted DVDs and I even checked again.

It also has a problem with a DVD folder structure - so something is messed up.

It's nice to know that at least someone has it working so it's worth my time to try.

Thanks.

---

### Post by Slacker3k on 2010-11-16
Taking another pass at this since I really would like to get this working.  I've now tested with a DVD that I created from home movies.  Works fine outside of storage groups, when I use it in a storage group the screen goes blank for a minute, then I'm taken back to the MythVideo gallery.

Any suggestions on what I could have wrong or how to troubleshoot?  I'm running 0.24 fixes now...

---

### Post by nickrout on 2010-11-16
> **Slacker3k said:**
> Taking another pass at this since I really would like to get this working.  I've now tested with a DVD that I created from home movies.  Works fine outside of storage groups, when I use it in a storage group the screen goes blank for a minute, then I'm taken back to the MythVideo gallery.

Any suggestions on what I could have wrong or how to troubleshoot?  I'm running 0.24 fixes now...

*sigh* what do your frontend logs say?

---

### Post by Slacker3k on 2010-11-16
The frontend log - while attempting to play an ISO:

libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso for reading
libdvdnav: vm: failed to open/read the DVD
2010-11-16 17:51:18.321 Failed to open DVD device at myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso
2010-11-16 17:51:18.364 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso for reading
libdvdnav: vm: failed to open/read the DVD
2010-11-16 17:51:18.380 Failed to open DVD device at myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso

---

### Post by Slacker3k on 2010-12-13
Thought I'd check in one more time and see if anyone else is having this issue.  I've tried many different ISO files including some that I made myself, and they all present the same symptoms.

---

### Post by finlay648 on 2010-12-18
I have the same issue that ISOs in the Videos storage group will not play. My frontend log shows a different problem that it is trying to use VDPAU when I don't have an Nvidia chipset that supports it. The thing that crashes the frontend is some kind of audio problem:

2010-12-18 20:13:29.786 [mp1 @ 0x7feb13c745e0]Header missing
2010-12-18 20:13:29.786 AFD Error: Unknown audio decoding error

I'm guessing that myth can't figure out the audio codec and the video rendering library to use.

ISOs in an NFS mount directory play just fine.

---

### Post by BicyclerBoy on 2011-01-06
Do you have libdvdcss2 installed ?
And ubuntu-restricted-extras   ?

Check you can then play a DVD in the optical drive via Mythtv.

---

### Post by tgm4883 on 2011-01-07
> **Slacker3k said:**
> The frontend log - while attempting to play an ISO:

libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso for reading
libdvdnav: vm: failed to open/read the DVD
2010-11-16 17:51:18.321 Failed to open DVD device at myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso
2010-11-16 17:51:18.364 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215
[B]libdvdread: Encrypted DVD support unavailable.
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso for reading[/B]
libdvdnav: vm: failed to open/read the DVD
2010-11-16 17:51:18.380 Failed to open DVD device at myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso

Storage groups don't support encrypted ISO's. This is in the release notes.

---

### Post by tgm4883 on 2011-01-07
> **finlay648 said:**
> I have the same issue that ISOs in the Videos storage group will not play. My frontend log shows a different problem that it is trying to use VDPAU when I don't have an Nvidia chipset that supports it. The thing that crashes the frontend is some kind of audio problem:

2010-12-18 20:13:29.786 [mp1 @ 0x7feb13c745e0]Header missing
2010-12-18 20:13:29.786 AFD Error: Unknown audio decoding error

I'm guessing that myth can't figure out the audio codec and the video rendering library to use.

ISOs in an NFS mount directory play just fine.

You should open a new thread for this issue and posts things like MythTV version

:EDIT:

Also, it's worth mentioning that you should post more logs (both frontend and backend). From what I can tell from what you posted, your issue is that the Header is missing and you have an Unknown audio decoding error.

---

### Post by Slacker3k on 2011-01-07
I'll report some more information when I get home, but I've had this issue with every release of 0.24 that I've tried.  And I upgrade a couple of times a week.  The ISO's play fine if I use a local directory without storage groups.

I also am testing using many different unencrypted DVDs, including Big Buck Bunny :-) [http://www.bigbuckbunny.org/](http://www.bigbuckbunny.org/) which should be completely "open".

I'll try and post more complete information soon.

---

### Post by scolbeck on 2011-02-09
I have the same problem where my unencrypted ISOs cannot play in storage groups.  They play fine from a NFS mount.  

Yesterday I opened bug 715548 ([https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/715548](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/715548)) for this problem.

---

### Post by Slacker3k on 2011-02-11
> **scolbeck said:**
> I have the same problem where my unencrypted ISOs cannot play in storage groups.  They play fine from a NFS mount.  

Yesterday I opened bug 715548 ([https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/715548](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/715548)) for this problem.

Doesn't look like that same issue.  I checked some of the ISOs that I have been testing with and ran them through AnyDVD, and it reports them as NOT CSS protected, region free with no protection.  So why do ALL of them still give me something similar to this?

libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso for reading
libdvdnav: vm: failed to open/read the DVD

This baffles me that anyone else on 0.24 isn't having this issue, but I have it on EVERY ISO I try... including ones I've authored myself.

---

### Post by Slacker3k on 2011-02-11
> **tgm4883 said:**
> Storage groups don't support encrypted ISO's. This is in the release notes.

I've mentioned several times, my ISOs are not encrypted.

---

### Post by nickrout on 2011-02-11
> **Slacker3k said:**
> Doesn't look like that same issue.  I checked some of the ISOs that I have been testing with and ran them through AnyDVD, and it reports them as NOT CSS protected, region free with no protection.  So why do ALL of them still give me something similar to this?

libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Could not open input: No such file or directory
libdvdread: Can't open myth://Videos@192.168.0.11:6543/Football-2007-08-27.iso for reading
libdvdnav: vm: failed to open/read the DVD

This baffles me that anyone else on 0.24 isn't having this issue, but I have it on EVERY ISO I try... including ones I've authored myself.

Are you SURE that you are using the Internal player for the iso playback? Those look suspiciously like mplayer error messages, although this is a bit of a guess.

---

### Post by Slacker3k on 2011-02-12
> **nickrout said:**
> Are you SURE that you are using the Internal player for the iso playback? Those look suspiciously like mplayer error messages, although this is a bit of a guess.


Yep - verified that the ISO file type is set to Internal.

---

### Post by nickrout on 2011-02-12
Try giving us a bit more of your logs - from the point where it says something like "Attempting to change from None to WatchingVideo"

---

### Post by nickrout on 2011-06-16
People might like to read this from the mailing list:

[http://www.gossamer-threads.com/lists/mythtv/users/483150#483150](http://www.gossamer-threads.com/lists/mythtv/users/483150#483150)

---

### Post by Al_Vampyre on 2011-06-17
> **nickrout said:**
> People might like to read this from the mailing list:

[http://www.gossamer-threads.com/lists/mythtv/users/483150#483150](http://www.gossamer-threads.com/lists/mythtv/users/483150#483150)

Nice one nickrout, I don't have an issue but that really is a great
find for those that do.

---

### Post by Slacker3k on 2011-11-04
Digging up this old issue of mine.  I was never able to solve this and figured I'd just try on the next release.  Upgrade to 11.10 and still had the issue (with both and upgrade and clean install.)

But.... I MAY have something.  Does anyone have their videos being served from a slave backend?  That's what I've been trying to do and it's never worked.  Then, today I tried it from my master backend and it works just fine.

So, I'm wondering if there's some issue with serving iso videos from slave backends, or if anyone can clue me in on why this is happening.

All my machines are now clean installs of 11.10, so I find it odd that it only works from the master since they should all be almost identical installs.

---

