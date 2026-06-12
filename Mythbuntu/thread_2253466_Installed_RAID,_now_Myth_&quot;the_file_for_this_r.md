---
title: "Installed RAID, now Myth &quot;the file for this recording can not be found&quot; and no record"
date: 2014-11-19
forum: Mythbuntu
---

### Post by todd-4 on 2014-11-19
Excuse the total ignorance, although I've been involved in command lines since DOS 3.0, I've never really dabbled in Linux until now.  Frustration over trying to make a Windows 8 media server induced me to try Mythbuntu.  The idea is to switch to something more bullet-proof, trouble free, and be done with the entire Windows dance for the rest of my life (at least on my media center...)

I've had it working off and on.  When it's working, I love it - but I keep "breaking" it as I work out the process of getting it to work the way I want.  Two steps forward, one step back every time I try to change something....  That's fine, good learning experiences, but now I've broken it in a way I can't seem to fix.

So... I had it running on a system with one HDD, and decided to put in a second drive and configure a RAID array.

ALL I did was back up the drive to external, create the RAID 1 array, format it and then copy everything back over.

NOW, if I bring up the Watch Recordings option I see all the recordings I made previously - before RAID - but if I attempt to play them I get "the file for this recording can not be found."

Also, if I try to set up a new recording, it appears to be recording - file is now listed in the Watch Recordings list - but if I try to play it - either during the recording or after it's done - I get the same "can not be found" error.

Also, when I look at the recordings list in Myth, it shows "0% of 0.00 GB" available - as if it can't even see the drive.  No new recorded file appears on the drive in the "recordings" folder either.

The drive is set up with multiple folders.  One (the one I set as "default") is called "recordings".  I have other folders on the drive for each of the other Myth recording paths - named the same as the setup in the backend.  For example, the folder I point LiveTV to is called "livetv", the folder for Fan Art is "fanart", etc, etc.

I thought perhaps a permissions issue, but if I open the drive and play with files on it it gives me no problems.  I can create things, delete things, etc in that folder so I assume I have the permissions I need.

If I watch a video in Myth, I see all the files in the "video" subdirectory and I can play them just fine.

Same with music in the "music" folder.  

Unless I'm missing something, it seems I have full access to the new drive.

FYI, this machine is set up with a separate boot drive (an SSD) so the only thing the RAID array is there for is storage of Myth data.

I have NO idea what information is important to give here to help in the troubleshooting so let me know if there's anything in particular that would be useful.

I don't really care so much about the old recordings - as far as I'm concerned I could just reformat the entire disc and start from scratch - but the inability to record new shows is a show-stopper....!

Before I go to that extreme, thought I'd ask.  

Now... I didn't just post here.  I did some searching and tried some things...   For instance, some posts refer to making sure the permissions are set at 777, so I did that.  no change.  Others talk about rebuilding the database - did that through the Control Center, no change.  Others mention making sure the host name is the IP address of the machine, done that, no change.

What am I missing?

Thanks,

Todd

---

### Post by Lester_Burnham on 2014-11-20
Hi,
We probably need to know the path to where your raid is mounted. Like /mythtv?
Have you gone into backend setup and modified the paths to point to the new locations? Like from /var/lib/mythtv/recordings to /mythtv/recordings if that is your new path?

Who owns the mythtv folders in the new raid? I normally copy the same permissions as the originals.
Lester

---

