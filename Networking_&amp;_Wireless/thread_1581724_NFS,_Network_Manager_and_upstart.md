---
title: "NFS, Network Manager and upstart"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by dvrvm on 2010-09-25
Hi,

I have the following problem:

There are three NFS mounts in /etc/fstab, which are automatically mounted. The network connection runs over NetworkManager. Since NWM brings up the network asynchronously, NFS doesn't mount correctly on the first try, but is loaded soon enough since *mount* automatically retries until it works. 

I can live with the fact that I have an error in my boot messages, since everything is up in time for the user. But, I need a (selfmade) upstart script which depends on the NFS mount being up. Even using "remote-filesystems" as the trigger doesn't help, because the trigger is apparently sent after the first failed try (I checked with cat /proc/mounts in my script, the nfs mounts are clearly not up.)

Can I somehow force the remote mounts to wait until NWM is up, or make the NFS mount emit an event when the mounts really get mounted?

---

### Post by SeijiSensei on 2010-09-25
> **dvrvm said:**
> Can I somehow force the remote mounts to wait until NWM is up, or make the NFS mount emit an event when the mounts really get mounted?

I asked a [similar question about Kubuntu]("http://ubuntuforums.org/showthread.php?t=1578316") the other day and got no replies.  I was trying to solve this problem by having networkmanager run a script after it sets up the connection.  It doesn't seem to work for me; how about you?

---

### Post by dvrvm on 2010-09-25
Hm. The idea is not bad. Actually, one could set up the mounts as noauto and have them mount "manually". To be really clean, I will make an upstart job which mounts the NFS mounts and which is started via initctl from the dispatcher, then have my original upstart script react on the mount upstart script being finished. I will try that tomorrow.

As for the format of the dispatcher script: it looks like an ordinary Bash script with the arguments $1 = interface and $2 = down or up, so basically you can do 

```

#!/bin/bash

if [ "$2" == "up" ]
then
  mount /blabla
  mount /blablub
fi

```

as a minimalistic solution (and of course make the entries noauto in fstab).

That dispatcher thing looks like a great tool, I didn't know about something like that existing...

---

### Post by SeijiSensei on 2010-09-25
> **dvrvm said:**
> That dispatcher thing looks like a great tool, I didn't know about something like that existing...

Well, it would be if it worked.  

I also tried putting the script in /etc/network/if-up.d/ whose components are run by the 01ifupdown script in /etc/NetworkManager/dispatcher.d/.  That doesn't seem to work either.

Here's what I'm running:

```
#!/bin/sh
TEST=`ifconfig | grep 'inet addr:192.168.1'`

echo "running as `whoami`; test returns $TEST" >> /tmp/dispatcher-log
echo "int=$1 and status=$2" >> /tmp/dispatcher-log


if [ "$TEST" != "" ]
then
    #ip route del 192.168.1.0/24 dev wlan0
    ip route add 192.168.100.1 via 192.168.1.1
    
    /etc/init.d/openvpn restart
    
    ip route del default
    ip route add default via 10.100.1.1
    
    #mount -t nfs -a
fi

exit 0

```

/tmp/dispatcher-log is never created nor written to, so it appears the script isn't executed at all.  I'm testing this by unchecking the rechecking the "Disable Wireless" option in KNetworkManager to bring the network down and then up again.

Works as advertised if I run it from the command prompt.

Maybe this just doesn't work with Kubuntu?  I've got a plain server installation running in a VM.  I'll try it out there.

---

### Post by kjohri on 2010-11-05
[http://www.softprayog.in/troubleshooting/linux/starting-network-server-after-interface-is-up.shtml]("http://www.softprayog.in/troubleshooting/linux/starting-network-server-after-interface-is-up.shtml")

---

### Post by larseko on 2010-11-05
I'm not sure if I have understood the problem, but would it help if you mounted the NFS shares thru autofs instead of fstab? That would ensure that the shares are mounted when a given directory/file is being accessed. Then you just have to make sure that the autofs daemon is started before your script is being run. 

I'm sorry if I've misunderstood completely. In that case, just ignore this ;-) Good luck. It's a while since OP first posted too, so you might have solved the problem.

---

### Post by silbak04 on 2010-11-05
> **SeijiSensei said:**
> Well, it would be if it worked.  

I also tried putting the script in /etc/network/if-up.d/ whose components are run by the 01ifupdown script in /etc/NetworkManager/dispatcher.d/.  That doesn't seem to work either.

Here's what I'm running:

```
#!/bin/sh
TEST=`ifconfig | grep 'inet addr:192.168.1'`

echo "running as `whoami`; test returns $TEST" >> /tmp/dispatcher-log
echo "int=$1 and status=$2" >> /tmp/dispatcher-log


if [ "$TEST" != "" ]
then
    #ip route del 192.168.1.0/24 dev wlan0
    ip route add 192.168.100.1 via 192.168.1.1
    
    /etc/init.d/openvpn restart
    
    ip route del default
    ip route add default via 10.100.1.1
    
    #mount -t nfs -a
fi

exit 0

```/tmp/dispatcher-log is never created nor written to, so it appears the script isn't executed at all.  I'm testing this by unchecking the rechecking the "Disable Wireless" option in KNetworkManager to bring the network down and then up again.

Works as advertised if I run it from the command prompt.

Maybe this just doesn't work with Kubuntu?  I've got a plain server installation running in a VM.  I'll try it out there.

Not 100% sure on this, but it seems to me that in your shell script you have:

```

/etc/init.d/openvpn restart

```One thing is, you have to be root. So you should have "sudo" in front of that...also the way you're doing it, should not be done anymore...because it is being deprecated. From now on, it should be done like this (in general):

```

sudo service my_service restart

```so go ahead and try putting this in instead of "/etc/init.d/openvpn restart":

```

sudo service openvpn restart

```or whatever it may be.

---

