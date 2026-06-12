---
title: "Use your NAS? How to make Testdisk write to a NAS."
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by baybe1111 on 2010-04-28
Hello nice world. I have a NAS which is nice:). I have a bad USB Disk on my PC which is not:(. As my PC's internal disk is small (embarrassing:oops:),I thought I could just copy a disk image of my bad USB drive onto my big NAS and either repair it or use photorec to recover the data. BUT neither Testdisk nor Photorec will "see" my NAS even though I can see it in nautilus, read and write OK. How do I make my NAS 'visible' to testdisk and photorec?:)

---

### Post by tgalati4 on 2010-04-29
Make a directory in your home folder:

cd
mkdir /my_bad_disk

mount (address of your NAS) /my_bad_disk

To get the address of your NAS, right-click on the drive in nautilus and select properties.

The you can copy stuff to /my_bad_disk and run photorec against it.

My mounting your NAS to a local directory, it behaves like a local/internal drive.

man mount for more details.

---

### Post by baybe1111 on 2010-04-29
Thank you, some progress has been made !. nfs was not there so synaptic fixed that. Now I get a different err or?

mount.nfs: DNS resolution failed for smb: No address associated with hostname

I tried my other nas and same? I used:

george@george-desktop:~$ sudo mount smb://bossnass/share/Recovered_files /home/george/my_bad_disk

Thanks for your help so far, I think I'm close now. Read man pages but couldn't see much?

---

### Post by tgalati4 on 2010-04-29
Edit your /etc/hosts file

sudo cp /etc/hosts /etc/hosts.bak
sudo nano /etc/hosts

Add the IP address of bossnass:

192.168.1.103  bossnass

Put in the correct address.  I just used a random example above.

---

### Post by baybe1111 on 2010-04-29
tgalati4 thank you, I have added both nas to hosts as below- did I put them in the right place? I still get the same error?

127.0.0.1	localhost
127.0.1.1	george-desktop
10.0.0.30	bossnass
10.0.0.16	mybookworld
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by tgalati4 on 2010-04-30
From the man page:

       The device indication.
              Most devices are indicated by a file name (of  a  block  special
              device),  like /dev/sda1, but there are other possibilities. For
              example, in the case of an  NFS  mount,  device  may  look  like
              knuth.cwi.nl:/dir.   It  is possible to indicate a block special
              device using its volume LABEL or UUID (see the -L and -U options
              below).


So your command might look like:

sudo mount bossnass:/share/Recovered_files /home/george/my_bad_disk

---

