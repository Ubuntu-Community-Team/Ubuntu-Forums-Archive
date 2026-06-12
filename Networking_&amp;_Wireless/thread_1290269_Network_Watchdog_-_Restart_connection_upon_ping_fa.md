---
title: "Network Watchdog - Restart connection upon ping failur"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Rich_B_uk on 2009-10-13
Okay guys & gals, hoping you can help.

I have a machine that I use as a gateway. This machine uses HSPA to connect to the net via a fully configured adapter (ppp0). 

I can fire up the connection in Networkmanager and all works well. Very occasionally however I will experience a lack of connectivity despite the face that I remain connected to the network according to NetworkManager. I'm putting this down to a very deep HW/SW glitch at my end, or some mast problem. I've tried it on multiple installs and it just seems to be one of those things that goes hand in hand with mobile broadband.

Anyway, to cut a long story short I require a daemon to run and ping a selection of 3 or so IPs every 5 mins. If they all come back as failed I can presume the net connection needs restarting. To do the restarting I can restart the entire networking subsystem, then use the command line network manager utility to instigate the connection once again (automatically connect doesn't work fantastically in my experience).

This thread (in particular the response from Pete Laughton) was helpful - [http://forum.soft32.com/linux/Program-reboot-computer-network-connectionftopic-487203-days0-orderasc-15.html](http://forum.soft32.com/linux/Program-reboot-computer-network-connectionftopic-487203-days0-orderasc-15.html)

Unfortunately I can't register for the forum because their SMTP server is FUBARed!

Anybody care to help me solve this issue? Is there a nice ready made script out there, can I cobble something together in cron, or am I completely off the mark? :)

---

### Post by Rich_B_uk on 2009-10-14
Still not having any luck with this. Damn my poor bash skills!

So in an ideal world my script would ping 3 different IPs in turn, and if packet loss on either link exceeded say, 10%, a set of actions would be taken to restart the link:

a) Restart networking
b) Restart networkmanager
c) Ask networkmanager to dial up my link again (using cnetworkmanager as a command line utility )

I have the latter commands, but am struggling to structure and build a script to perform the above logic.

Any gurus fancy offering their kind assistance?

---

### Post by fishy6969 on 2009-10-15
How about something like -

```
#!/bin/bash
HOSTS="host1 host2 host3"

# no ping request
COUNT=10

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -lt 8 ]; then
    # ie 70% failed
        myrebootcommandhere
  fi
done

```

---

### Post by fishy6969 on 2009-10-15
This should aggregate the replies from all the pings.

```

#!/bin/bash
HOSTS="host1 host2 host3"

# no ping request
COUNT=10
RECCOUNT=0
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
 
  RECCOUNT=$(($RECCOUNT + $count))
done
if [ $RECCOUNT -lt 15 ]; then
    # ie 70% failed
        myrebootcommandhere
fi

```

---

### Post by Rich_B_uk on 2009-10-15
fishy6969 - fantastic. I really wish I was able to do this kind of stuff myself but I find scripting quite difficult for some reason.

Can you talk me through the counts so I understand and am confident with it?

So we set the count to 10, to ping that many times. That goes into the ping function and follows the -c switch to set that.

Reccount is calculated by initially setting the variable to 0 and then for each host pass, adding the amount of successful pings on. So on my first pass perhaps 7 pings are received, wheras on my second pass none are received, and finally with the last host, all pings are received. That would make reccount 17.

I just don't really understand the -lt command at this point. It looks inside the Reccount variable and if it's... more? less? than 15 it triggers the restart command. Sorry, I'm clueless at that point because I can't see my usual <=> notations.

Sorry for being thick, but I am learning and your help is appreciated. There's relatively little on the net out there to help with this and so I hope in the future people will find this thread useful! :popcorn:

---

### Post by fishy6969 on 2009-10-15
> So we set the count to 10, to ping that many times. That goes into the ping function and follows the -c switch to set that.

Reccount is calculated by initially setting the variable to 0 and then for each host pass, adding the amount of successful pings on. So on my first pass perhaps 7 pings are received, wheras on my second pass none are received, and finally with the last host, all pings are received. That would make reccount 17.

Spot on.
> I just don't really understand the -lt command at this point. It looks inside the Reccount variable and if it's... more? less? than 15 it triggers the restart command. Sorry, I'm clueless at that point because I can't see my usual <=> notations.
'-lt' means less than. There's a good reference guide here -
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

Regards

---

### Post by Rich_B_uk on 2009-10-15
Cheers for all your advice. Appreciated.

---

### Post by Rich_B_uk on 2009-10-16
By complete chance I found a similar/identical script here - [http://www.cyberciti.biz/tips/simple-linux-and-unix-system-monitoring-with-ping-command-and-scripts.html](http://www.cyberciti.biz/tips/simple-linux-and-unix-system-monitoring-with-ping-command-and-scripts.html)

There is one last problem, and that's with the way ping itself operates. Say my net connection has completely dropped out, and I run a ping command with a count of 4. Instead of the behaviour exhibited with other ping variants where the output would be four instances of "General Failure" (Windows) or "Timed out" followed by the same summary line displaying transmitted/received/packet loss %/total time - ping on my Ubuntu 9.04 install simply returns a single line:

```
connect: Network is unreachable
```

Because of this the script breaks. It doesn't grep out the amount of received packets because that status line isn't printed. 

I suppose I either need to precede this script with a statement that checks to see if the output is "unreachable", in which case it runs the reset scripting, otherwise it goes on to do the ping count additions.

Ideas?

---

### Post by fishy6969 on 2009-10-16
> By complete chance I found a similar/identical script here - [http://www.cyberciti.biz/tips/simple...d-scripts.html](http://www.cyberciti.biz/tips/simple...d-scripts.html)

I've been rumbled!

[http://www.commandlinefu.com](http://www.commandlinefu.com) is another place for good scripting tips

The variable $? returns a code for the success or failure of a program, 0 being successful and every other higher number will be a failure. After the ping command you could insert a test ie

```
if [ $? -ne 0 ]
then
    rebootnetworkcommand
    exit
fi
```

---

