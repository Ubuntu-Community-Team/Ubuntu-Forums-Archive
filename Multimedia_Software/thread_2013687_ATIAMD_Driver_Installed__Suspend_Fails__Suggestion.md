---
title: "ATI/AMD Driver Installed | Suspend Fails | Suggestions?"
date: 2012-07-01
forum: Multimedia Software
---

### Post by neu5eeCh on 2012-07-01
And... on to the next problem.

Having successfully installed and tweaked video driver and video playback performance, I find that *Suspend* no longer works. I'm going to start googling now, but any suggestions are welcome.

Xubuntu 12.04 | **Mobility Radeon HD 3650 **|64bit | Sony VAIO VGN-FW373J

---

### Post by neu5eeCh on 2012-07-01
Yeah. OK. Cold shoulder, eh? I get the message. ;) I filed a bug report [here]("https://bugs.launchpad.net/bugs/1019862").

---

### Post by Toz on 2012-07-01
Hi VTPoet. What does /var/log/pm-suspend say? Also, run the following command to see if there is anything related in syslog:
```
cat /var/log/syslog* | grep PM:
```

On a long shot (mostly because its worked on other Sny vaios), have you/can you try: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")?

---

### Post by neu5eeCh on 2012-07-02
> **Toz said:**
> Hi VTPoet. What does /var/log/pm-suspend say? Also, run the following command to see if there is anything related in syslog:
```
cat /var/log/syslog* | grep PM:
```On a long shot (mostly because its worked on other Sny vaios), have you/can you try: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)?

Hi Toz, I just saw your response. I ran your command in terminal, but the output goes on a bit. How do a post this stuff without using up the whole page? I notice that some here post clickable extracts.

**Edit:** I tried the link you provided, but unfortunately it didn't work on my system.

---

### Post by Toz on 2012-07-02
> **VTPoet said:**
> Hi Toz, I just saw your response. I ran your command in terminal, but the output goes on a bit. How do a post this stuff without using up the whole page? I notice that some here post clickable extracts.
Try:
```
pastebinit /var/log/pm-suspend
```
...and post back the link that gets generated.
> 
**Edit:** I tried the link you provided, but unfortunately it didn't work on my system.

Here it is in a nutshell:
1. Create a file:
```
gksudo leafpad /etc/pm/sleep.d/20_custom-ehci_hcd
```

2. Copy/Paste the following code to the file:
```

#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19
#...and http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug    
# tidied by tqzzaa :)

VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}

bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}

case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac
```

3. Save the file.

4. Make the file executable:
```

sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```

5. Try suspend again.

This code unloads specific usb modules prior to suspend (and reloads them on resume) that can be problematic on some systems that have suspend issues.

---

### Post by neu5eeCh on 2012-07-02
Thanks again. I tried the script but, in my case, it didn't help.

My impression is that this problem is directly related to the video drivers.

I also tried the pastebinit command but the terminal responded that it was "Unable to read from: /var/log/pm-suspend"

---

### Post by Toz on 2012-07-02
oops, my bad. It should be:
```
pastebinit /var/log/pm-suspend.log
```

Lets see if there's anything in the log file. If not, we can go deeper down the rabbit hole and get more debugging info.

---

### Post by neu5eeCh on 2012-07-02
> **Toz said:**
> oops, my bad. It should be:
```
pastebinit /var/log/pm-suspend.log
```Lets see if there's anything in the log file. If not, we can go deeper down the rabbit hole and get more debugging info.

Oh... that's kewel! Never done this before. The link to the log is [here]("http://paste.ubuntu.com/1072238/").

---

### Post by Toz on 2012-07-02
Ok, nothing there. Let's go deeper.

```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend

```

After you recover, post back the link to your /var/log/pm-suspend.log file (it will be considerably larger).

EDIT: Had a look at your bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019862/comments/27]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019862/comments/27")). When you run 'dmesg > dmesg.txt', it will create a dmesg.txt file. Post that one back as well (and attach to bug report). There might be some useful info in there.

---

### Post by neu5eeCh on 2012-07-02
OK. I'll do that tomorrow. I'm burned out for tonight. I had installed the upstream kernel. When I received the installation error message (vis-a-vis the upstream kernel), I assumed I couldn't use it. Silly me. I rebooted and didn't realize I was running it because I didn't pay attention to grub. The upstream kernel deactivated my FGLRX install. Had to uninstall the upstream kernels and reinstall AMD's drivers. What a mess - but my own doing.

---

### Post by neu5eeCh on 2012-11-18
Solved!

The solution can be found at Xubuntugeek:

[http://xubuntugeek.blogspot.com/2012/11/solved-suspend-causes-reboot-on-sony.html](http://xubuntugeek.blogspot.com/2012/11/solved-suspend-causes-reboot-on-sony.html)

**Fix**

   Edit (with root permissions) the line GRUB_CMDLINE_LINUX on the file /etc/default/grub, adding the option acpi_sleep=nonvs. 

[IMG]https://lh4.googleusercontent.com/-u9O0PA57OTs/UKKySqA7RBI/AAAAAAAADDU/V9weunve6ZY/s500/vaio-suspend.png[/IMG]

Then sudo update-grub2

---

