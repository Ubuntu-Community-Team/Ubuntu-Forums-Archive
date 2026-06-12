---
title: "Tricks to make life easier..."
date: 2010-03-20
forum: Mythbuntu
---

### Post by timconradinc on 2010-03-20
I was reading [this thread]("http://ubuntuforums.org/showthread.php?t=1434476") and did a quick search to find [this thread]("http://st-on-it.blogspot.com/2008/02/how-to-defragment-your-xfs-partition.html") and started following the instructions on the latter. I was going to start the instructions in the later, only to start the session in a 'screen' session so that it'll keep running. And, I thought there might be others that find some of these tools helpful.

Screen is a tool in unix/linux that will keep a process running after you detach from the session. In other words, if I start a copy of a file on my mythtv box, and my laptop goes to sleep, the copy will continue, even though the putty session has died. I use it on any reasonably long-running process, since it's really annoying to get disconnected 90% through. To install, just run:
```
sudo apt-get install screen
```

Run 'screen' at the command line, and use control-a, c to create additional terminals, control-a, n to go to the 'next' terminal, and control-a, d to 'detach' from the currently running screen. The next time you login, just run screen -r. If screen -r tells you that a process is still attached, run screen -D -RR to override.

Screen does take some getting used to, but it's a very powerful tool.

A second tool that I find really useful is '[rsync]("http://samba.anu.edu.au/rsync/")'. Rsync is great for synchronizing different directories, either remote directories or local directories. After having some difficulties with my RAID recently, I've started keeping a local backup on an external USB drive with the following in a crontab:
00 05 * * 2 /usr/bin/rsync -av /share/Movies /share/Backups/a/Movies
Every 2nd day of the week (which is Tuesday, I think), the /share/Movies directories changes are copied to /share/Backups/a/Movies.

To install, just run the following:
```
sudo apt-get install rsync
```

Are there other linux tools that people find useful specifically for MythTV installations?

---

### Post by SiHa on 2010-03-21
monit is also a very useful tool. As the name suggests, this will monitor a process (or pretty much anything else) and restart it if it dies, or stops responding.
Very handy on my old 0.21 backend that kept dying quite frequently.

---

