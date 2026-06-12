---
title: "Great explanation of mythtv file permissions and propagation"
date: 2021-02-05
forum: Multimedia Software
---

### Post by vidtek on 2021-02-05
I cannot claim credit for this---I found this little gem over at [https://lists.mythtv.org/pipermail/mythtv-users/2018-May/396231.html]("https://lists.mythtv.org/pipermail/mythtv-users/2018-May/396231.html")

This will assist many to get their heads around a very difficult aspect of mythtv.

I am waiting on a response from Mythtv.org to advise the developer responsible for this great piece.  I will edit and attribute when I know more.

[B][I][LEFT]I have not used NFS much, but it looks like it has the same problem as
SAMBA/CIFS - the user IDs and group IDs (apart from root = 0) do not
match between machines.  That makes it difficult to get ownership to
work, unless NFS has some mechanism to map the user IDs and group IDs
to get them to match.  So you probably will need to use wide open
permissions instead.  As in everybody having access (chmod a=rwx). But
have a look as the NFS documentation and do a web search to see what
your options are for getting correct ownership.

Using network drives is fine for read-only things, such as videos,
pictures and music.  And there should be no problems for the small
writeable files for things like the metadata and artwork.  But the
higher bandwidth, and time critical, writing of recordings can be a
problem.  Looking at the numbers for the bandwidth of one HD DVB-T
recording from my channels, I seem to need about 10 Mbytes/s or 80
Mbit/s for one recording.  So being generous and allocating 100
Mbit/s, you would think that a 1 Gbit/s Ethernet would be fine for up
to 10 recordings at once.  But that ignores other traffic, and unless
the NFS recording traffic has its packets flagged as high priority and
the switch between the backend PC and the NFS box does QoS and gives
those packets priority over other traffic, then you will have a
problem with just one recording if something else is using all the
bandwidth it can get.  Just you copying a file to the NFS box from
another device can use all the available bandwidth on the NFS box's
one Ethernet port, and has the potential to cause gaps in your
recordings.  Doing backups to the NFS box (a common use for such a
box) is very likely to cause trouble unless the backup software has
options to be set to use lower bandwidth, or can be set to only do
backups when there will never be any recordings happening.

So I would suggest doing some serious testing to see if it is OK to
record directly to the NFS box before setting it up that way.  How
many recordings at once do think you will be doing?  How many tuners
do you have?  How many multirec recordings will each tuner do at once?

An alternative is to record to a local drive on the mythbackend box,
and when each recording completes (or later), move it over to the NFS
box.  To make that work, you set up another storage group (other than
"Default") and put the NFS recording directories in that storage
group.  I have one like that called "Archives", for my 8 Tbyte
shingled drives that can not be used for recordings as they can just
stop for several seconds while they do a shingle re-write operation.
Then you put the local hard drive directories in the "Default" storage
group, and if you never create any recording rules that use the
"Archives" storage group, nothing will ever be recorded to that
storage group, but anything you move into the "Archives" storage group
will be visible to mythbackend and can be played and deleted.

I have written myself some Python for moving files to my archive
drives.  It keeps a check on MythTV activity and stops moving files
when a recording starts or just before the next one is scheduled to
start.  It is probably not quite what you would want for moving files
from your backend local drive(s) to NFS, but I would be happy to
modify it to do what you need if you decide to go that way.

Even with a local recording drive, if it is spinning rust I use a rule
of thumb that there should be no more than three recordings going to a
drive at once.  The problem is about the time taken for head movements
between the recording files, and also to the directory areas when the
file needs to be expanded.  And it is even worse if your system and
database are on the same drive.  Then I would do no more than two
recordings at once.  Modern hard drives have very fast write speeds,
but the head movement has not sped up nearly as much as the on-track
write speed has, so it is easy to get fooled by the fast write speed
in the specification.

Of course, if the local drive is an SSD, then you can usually write to
many more files at once as there is no head movement.  All you have to
watch out for there is the problem of the erase times.  If the spare
space on an SSD has already been erased, its write times are very
fast.  But if the drive is using a weekly TRIM operation to do the
erasing (which is the default in Ubuntu), then the large file sizes of
recording files can cause it to run out of erased blocks and have to
do a block erase before each block write.  That makes an SSD write
very slowly.  So if you record to SSD you should either be using the
"discard" option on the SSD when it is mounted from fstab, or running
the fstrim cron job much more often.  I run my fstrim cron job daily,
but I do not record to the SSD - it just gets a lot of database
activity.
[/LEFT][/I][/B]

Told you it was good eh?

Cheers Tony.

---

