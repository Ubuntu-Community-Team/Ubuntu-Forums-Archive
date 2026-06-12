---
title: "Citrix woes persist"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by ngronewold on 2010-04-04
I'm having a hell of a time getting connected to my company's server via Citrix.  It worked perfectly prior to a trip I took overseas, but once I returned I found it's no good anymore.  I suspect a recent automatic update recommended by Cannonical messed it up.

I have Citrix Receiver installed fine.  I can also log into my company's Citrix page, no sweat. But when I select <full desktop> after about 2 seconds I get the error box with message <Network or dial-up problems are preventing communication with the server>. It counts down to an automatic retry or gives the option to quit.

We are an online publishing company.  I use Citrix to look at the company's story budget, to make sure I don't write an article on a subject that someone else is working on.

I'm running 9.10.  Basically a newbie as I've been wedded to Windows my whole life but bailed out after suffering the nightmare that was Vista.

Our techies are stumped. Any ideas?


Nate

---

### Post by gzarkadas on 2010-04-04
I have never used this stuff, so I doubt if I will eventually be of any help, but it will be useful in order to get help by others to open the view logs application, select 'syslog', scroll to the end and then try to connect to Citrix, as you described. Watch the syslog output for any suspicious messages that may spot the cause of the error and post them here so someone can figure what's happening.

---

### Post by ngronewold on 2010-04-04
OK, just tried it.  This is the only new line that pops up in syslog after I try and again fail to connect:

Apr  4 11:59:04 Nate wpa_supplicant[947]: CTRL-EVENT-SCAN-RESULTS


Does this tell us anything?

---

### Post by gzarkadas on 2010-04-04
Do you use a wireless connection to access the Internet? If so this line may indicate a problem with your wireless card driver (if it has firmware maybe the latest kernel updates outdate it?). If you use an ethernet connection or if your other network activities are just fine, then ignore it. 

Other places to check:

1. Go to System|Administration|Users and Groups|select your account from the list|go to 'User Privileges' tab|verify that 'Connect to wireless and wired networks' is checked. This showed up to me after a recent kernel update and temporarily made me wonder why my connection did not work.

2. Find how your Citrix app uses the network to connect. Does it uses a VPN? some kind of proxy? other? Verify that all those components and ports are working.

3. Review your firewall rules. Maybe some line has changed and blocks a port used by your Citrix app?

4. Examine /var/dpkg.log (and also maybe the _.1 _.2.gz, etc log archives)  to try find what was the software that was installed just before you lost the connectivity to Citrix.

5. If you have a recent backup of /etc before the day that Citrix stopped working unpack it in a separate folder (say /old-etc) and compare them with your current config to see what has changed. Use:
```

find -O3 /etc -type f -ls > ~/current-etc.files
find -O3 /old-etc -type f -ls > ~/old-etc.files
diff ~/current-etc.files ~/old-etc.files

```This will show both added|deleted and changed files.

---

### Post by ngronewold on 2010-04-04
Thanks.  I connect wirelessly but am having no problems with any other online applications. Right now I'm on the computer that's experiencing the problem and the Internet is just as blazing as usual. But you were right -- "Connect via wireless and ethernet" was unselected in System Administration, for some strange reason.  But, after setting it right I still can't get in.

I'm beginning to think the problem is on their end.  My company uses all Windows and as far as I know I'm the only one on a Linux system.  It may be that a recent security firm-up they did while I was away overlooked poor little ol me.  I'm going to ask them about VPN before checking the firewall.

Really appreciate the help.

---

### Post by ngronewold on 2010-04-04
Just FYI, I tried your #5 suggestion just for kicks. Here's what it shows.  You'll take note of the system's objection to my sloppy typos:

ngronewold@Nate:~$ find -03 /etc -type f -ls > ~/current-etc.files
find: unknown predicate `-03'
ngronewold@Nate:~$ find -O3 /etc -type f -ls > ~/current-etc.files
find: `/etc/chatscripts': Permission denied
find: `/etc/ssl/private': Permission denied
find: `/etc/cups/ssl': Permission denied
find: `/etc/ppp/peers': Permission denied
ngronewold@Nate:~$ find -O3 /old-etc -tupe f -ls > ~/old-etc.files
find: unknown predicate `-tupe'
ngronewold@Nate:~$ find -O3 /old-etc -type f -ls > ~/old-etc.files
find: `/old-etc': No such file or directory

---

### Post by ndefontenay on 2010-04-04
Hi.

You might want to do those commands again by prefixing it with sudo like this:
sudo find -03 /etc -type f -ls > ~/current-etc.files

This will prompt you for your password and you will access the restricted folders.

Nico

---

### Post by ngronewold on 2010-04-04
Can't believe I forgot about "sudo".  But still didn't matter much.  No reaction to the first request.  Second came up "no such file" for /old.etc

---

### Post by gzarkadas on 2010-04-05
> **ngronewold said:**
> Can't believe I forgot about "sudo".  But still didn't matter much.  No reaction to the first request.  Second came up "no such file" for /old.etc

This is because you first have to unpack your backup (which you also must have done explicitly; there are no set-up auto-backups in a standard installation) into this folder and create it (it does not exist in a standard linux installation). 

Now, I don't know which backup method you use, but assuming it can be done from the command line, here is the full sequence of commands (you will have to fill-in the pieces inside <> as this: <foo> -> bar):
```

sudo -i
mkdir /old-etc
<command to unpack your backup to /old-etc>
find -O3 /etc -type f -ls > /root/current-etc.files
find -O3 /old-etc -type f -ls > /root/old-etc.files
diff /root/current-etc.files /root/old-etc.files > /home/<your account>/etc.diff
chown <your account>:<your account> /home/<your account>/etc.diff
rm /root/current-etc.files /root/old-etc.files
exit

```The exit at the end is to close your root session; it will not close your terminal window.

After that you will be able to open etc.diff in your home folder with any method you like.

When you are done with all of the inspection, you can delete the /old-etc folder (again you will have to use your root-wear) with:
```

sudo rm -R /old-etc

```

---

