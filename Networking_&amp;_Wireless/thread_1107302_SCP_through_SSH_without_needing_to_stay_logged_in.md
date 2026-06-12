---
title: "SCP through SSH without needing to stay logged in"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by Ynothna on 2009-03-26
Hi,

I've been trying to backup some files from a remote server and been having some trouble. I know I'm over complicating matters with the method I'm using, but it's become one of those "I wonder if I can make it work" things.

Basically I'm running SSH through 3 machines. The remote server, my server, and my laptop. The remote server has the files I want a copy of, my server is where I want the files to end up, and my laptop is where I'm sending all the commands from. Easy enough so far.

Where I run into the problem is with SCP. Using SSH I tell the remote server to send the files (or the local server to pull the files) via SCP. My problem is the process is going to take several days (I have a lot to pull across) and I take my laptop to and from work with me everyday, so leaving it connected and running the SCP process is not possible. I need to be able to use my laptop to tell either of the servers to run the SCP command and then be able to log my laptop out of the system after and still have SCP copying the files.

I know the easy way would be to hook up a monitor and keyboard to my server and just run the command there and leave it, or use CRON, but I want to see if I can make it work from my laptop, more for learning purposes then anything else.

Is this something that's possible or am I just beating a dead horse?

Thanks for any help.

Ynothna

---

