---
title: "Creative Zen Vision:M- Is mtpfs *supposed* to not work w/ mv?"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by violagirl23 on 2008-01-21
I am not an Ubuntu user, but a Gentoo user, and I installed mtpfs and all its dependencies from source (via Portage), but since my question is almost more like a poll, asking other users with the same device if they have this issue as well, I thought it'd be best to post in a forum with a great deal of users, such as the Ubuntu forums.
I do not actually know if this is a personal problem, or just a general overall limitation with mtpfs (or perhaps it would be with fuse, or even libmtp... not sure where the problem would arise from).
I cannot use the mv command with my Vision:M within the player.  So let's say I had a folder /mnt/zen/foo/foo.mp3.  I could not be in the folder and use the command mv foo.mp3 foo2.mp3 nor the command mv foo.mp3 ../foo2.mp3 (to move it to the directory above).  I CAN, however, do things like mv foo.mp3 ~violagirl23/Desktop/foo2.mp3.  It's obviously just moving WITHIN the player that causes trouble.  It spits up the following error:
mv: cannot move `foo.mp3' to `foo2.mp3': Function not implemented
It also spits up errors about timestamps not being able to be preserved if I did, say, cp foo.mp3 foo2.mp3.  So the file WILL copy, but it spits up
cp: preserving times for `foo2.mp3': Function not implemented
It will NOT copy, however, if foo2.mp3 already exists, only if it doesn't.  Otherwise it just spits up function not implemented at me and refuses to copy.
Of course I can still get things done.  For instance, whenever I want to rename a file, instead of typing mv foo.mp3 foo2.mp3, I can type cp foo.mp3 foo2.mp3 && rm foo.mp3.  This will work.  But it SURE is a hassle.  And it also prevents me from renaming via the window manager; I HAVE to do it via terminal.
I have also noticed I cannot delete things via the window manager and have them go to the trash bin... it spits up another Function not implemented at me.  I have to use <Shift><Del> to bypass the trash can to delete files.

So my question is, are these problems normal, or can other Vision:M members use these commands without problems?  I can't figure out exactly what is causing these Function not implemented errors.  I suppose.. when you move stuff around and copy it around on an mp3 player, it is using mtp, so the purpose of mtpfs would be to act as a middle-man to interpret your shell commands into things mtp can understand, right?  So is it possible mtpfs just isn't written to allow you to use commands like mv within the player?  That it doesn't have any function to call to translate to the mtp language the mp3 player needs, so it just pops up Function not implemented?
Basically, is this normal for the Creative Zen Vision:M, or am I an oddball out here?  Could some other Vision:M users tell me their experience with this?
Because I am slightly concerned that my hack job on the permissions for /usr/bin/mtpfs and /usr/bin/fusermount might be what is causing these problems, though probably not (it doesn't work as root either).  I had to hack at it because the fuse group was not created when I installed it, so I had to make my own fuse group and hack away at the permissions to get it to work.
Here are the current permissions (it's the same for both files):
-rwsrwxr-- 1 root fuse 22256 2008-01-19 17:41 /usr/bin/mtpfs
I had it as -rwsr-xr-- before, which I will probably change it back too.  I had just been wondering if g+w would allow me to use mv.. but alas, it did not work.
In addition, I have to type mtpfs -o user=violagirl23 (now aliased) to let myself USE fusermount -u as a non-root user... some sort of bug in fuse I guess, or else it throws up at me that the device is not listed in /etc/mtab, and this is the workaround.
So I guess my general question is... is this problem with mv normal, and if so, are there any plans to make it implemented in the future?

---

