---
title: "SSH copying files suddenly slowed to 1/30th speed"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2009-12-14
Hi guys

I have an Ubuntu 8.10 machine in my loft, which is my torrent server. It will happily download at 1MB/s from the internet.

I connect into it from an Ubuntu 9.10 machine, using SSH to copy files, via nautilus.

For the past year, I have been getting file copy speeds of 1-2 MB/s, which meant a 350MB video took 5 minutes to copy.

Since Friday, for some reason, the copy speed has crawled to 30-40 KB/s. Meaning it would take hours or even days to copy a 350Mb file.

So questions are, what has happened, and how to fix ? I have kept the 9.10 machine as up to date as possible, so it's had 3 kernel updates, since upgrading. However when I boot into a previous one (GRUB2 leaves them all in) it's still as slow.

I can connect into it using NXClient, as before, and that's fine, and it's still downloading at fill speed, so it's not something stealing bandwidth ... just the SSH copy. I tried deleting the connection and re-creating it, but it didn't fix it.

One thing which may or may not be significant is just before I had this problem, I ran out of disk space on the download machine. This was because deleting files in NXClient seems to shift them into the root trash folder. I had to clear that out, and now I have 20Gb free. However is it possible a cache or swap file has been borked and needs fixing ?

---

### Post by Lars Noodén on 2009-12-14
What does the (sanitized) tracerout output look like?  Try it both without dns lookups and with.

```

# without dns it should be faster
/usr/sbin/traceroute -n *remoteserver*

# with dns it should be slower
/usr/sbin/traceroute -n *remoteserver*

# if there are bad problems, try tcp packets to port 22
sudo /usr/sbin/traceroute -T -p 22 -n *remoteserver*

```

---

### Post by MaindotC on 2009-12-14
This has nothing to do with Ubuntu or any settings to your machine, based on the information you've provided.  It could be another machine on your network, limitations by your ISP, or any other number of factors but it has nothing to do with Ubuntu.

---

### Post by Jethro_uk on 2009-12-15
> **strAlan said:**
> This has nothing to do with Ubuntu or any settings to your machine, based on the information you've provided.  It could be another machine on your network, limitations by your ISP, or any other number of factors but it has nothing to do with Ubuntu.

I'm talking about an internal network copy ... my ISP has nothing to do with it. As I said, download speeds to the "upstairs" machine from the internet are fine ... as good as ever.

I'm at work now, but I'll try rebooting my (wireless) router. I know sometimes they can cause problems.

---

### Post by ubu_can on 2009-12-15
It looks like it happened to my 9.04 -64bit distro as well. New update 2.6.28-17-generic crawls to 20 KB.... I booted on the previous (2.6.28-16-generic), it is back to about 6 MB (bytes). Now I lost my nvidia driver, I have to find a way to get it for the new kernel.

I also noticed that my external usb drives were not mounted automatically, as they used to before. I do not know whether this has to do with the new kernel, though.

---

### Post by Jethro_uk on 2009-12-15
Right,

I managed to log into the upstairs machine, and tried to "push" the files to the downstairs machine using Nautilus - same result.

Then I tried using scp ... it started at 2MB/s !!!!!!

And over 1 minutes slowed down to ... yup about 25/30 Kb/s


So whatever this issue is, it's cumulative, and probably something to do with a protocol snafu ... beyond that ...

---

