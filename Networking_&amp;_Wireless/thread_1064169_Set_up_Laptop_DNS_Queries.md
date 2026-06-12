---
title: "Set up Laptop DNS Queries"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by mlissner on 2009-02-08
I want to make my laptop have some sort of tiered hosts.conf file, so that queries to a certain host will first be internal, and failing that, queries will do the normal external DNS request. 

So, for example, say I query my email server: mail.example.com. First, it tries the internal IP address where it would be if I am currently in my office, which is static, and is 192.168.1.1. If that fails, it performs a DNS lookup of the server, and uses that. 

Is there a way to set this up? The idea is that I'm usually in my office, and doing the DNS lookup, over the internet routine is very slow when I can just query my mail server over the intranet instead. When I take my laptop outside the office though, it still needs to work.

---

### Post by ugm6hr on 2009-02-08
Not an expert, but you can add IP addresses to /etc/hosts

You also need to ensure that /etc/nsswitch.conf lists "files" as the first in the hosts line (before dns).

---

### Post by mlissner on 2009-02-08
Is there a way to do that though that will work whether I'm on the Intranet or not? That was my first instinct too.

---

### Post by ugm6hr on 2009-02-08
I don't know.

Thinking about it, it would try the /etc/hosts specified IP automatically, and then error if there was nothing there.

Similar issue for accessing the (unfortunate) website with the fixed IP of 127.0.0.1 (which is aliased as localhost in Ubuntu).

---

### Post by mlissner on 2009-02-09
OK, here's a first effort at a solution. You put the following in a script:
```
% more switchHosts.sh 
#!/bin/bash
# A script to switch the configuration of /etc/hosts with a different file. 
# Not the best method to configure things, but it might just work.


while true
do
  #First, we check if we are connected to pizzapuppysantaclaus
  #If grep has a hit, we're connected, and $? will equal 0, if not, $? will equal 1
  iwconfig 2> /dev/null | grep pizzapuppysantaclaus > /dev/null


  if [ $? = 0 ]
  then
    #Switch the /etc/hosts file with the other one
    cp -f /etc/hostsIntranet /etc/hosts
    sleep 3000
  else
    #Switch the /etc/hosts file with the other one
    cp -f /etc/hostsInternet /etc/hosts
    sleep 6000
  fi
done

exit 0

```

You set the script to run at startup. If your SSID is pizzapuppysantaclaus, you're at home, so you switch to Intranet configuration, and wait* five* minutes to check again. If you're SSID is not pizzapuppysantaclaus, you're away from home, and so you switch to that config, and wait *ten* minutes. 

The wait times are different because in the former case, your connection to the server is a bit slower, which is OK, but in the latter case, you have no connection to the server, and need to switch, preferably soon.

Thoughts?

---

### Post by mlissner on 2009-02-09
Alright, as a bump, I'll post the second version of the script:
```
#!/bin/bash
#A script to switch the configuration of /etc/hosts with a different file. 
# Not the best method to configure things, but it might just work.


if [ $# -eq 0 ]
then
    while true
    do
        #First, we check if we are connected to pizzapuppysantaclaus
        #If grep has a hit, we're connected, and $? will equal 0, if not, $? wil
l equal 1
        iwconfig 2> /dev/null | grep pizzapuppysantaclaus > /dev/null


        if [ $? = 0 ]
        then
            #Switch the /etc/hosts file with the other one
            cp -f /etc/hostsIntranet /etc/hosts
            sleep 3000
        else
            #Switch the /etc/hosts file with the other one
            cp -f /etc/hostsInternet /etc/hosts
            sleep 6000
        fi
    done

elif [ $# -eq 1 ]
then
    case "$1" in
        --intranet|-i)
            gksudo 'cp -f /etc/hostsIntranet /etc/hosts';;
        --internet|-I)
            gksudo 'cp -f /etc/hostsInternet /etc/hosts';;
    --list|-l)
        more /etc/hosts;;
    esac
else
    echo "switchHosts.sh: Invalid number of arguments"
    echo
    echo "Usage: switchHosts.sh [option]"
    echo
    echo "--internet, -I"
    echo "    Switch to Internet mode"
    echo
    echo "--intranet, -i"
    echo "    Switch to intranet mode"
    echo
    echo "--list, -l"
    echo "    Show the current value of /etc/hosts"
fi

exit 0

```

---

### Post by mlissner on 2009-02-20
So, I've moved that script to /etc/init.d/switchHosts, and I've run update-rc.d switchHosts defaults.

Root starts the script when the computer starts, but it doesn't work. Any ideas on why, or how to fix it?

---

### Post by mlissner on 2009-02-20
I finally figured this out with some help from IRC. Here's the final solution: [http://michaeljaylissner.com/blog/location-based-dns-switching-for-intranet-vs-internet](http://michaeljaylissner.com/blog/location-based-dns-switching-for-intranet-vs-internet)

---

