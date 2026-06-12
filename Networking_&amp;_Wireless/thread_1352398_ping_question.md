---
title: "ping question"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by SmarterThanMyPhone on 2009-12-11
Whats the buntu equivalent of ctrl+pause break for a running ping?

---

### Post by chili555 on 2009-12-11
Ctrl+C

Or, even better, you could instruct ping to run for a specific count:```
ping -c3 www.google.com
```Also see:```
man ping
```

---

### Post by SmarterThanMyPhone on 2009-12-18
ctrl +c just kills it, same as windows. I'm trying to keep the ping running but show the stats so far. I'm trying to monitor my DS3 over a long period of time and collect stats at intervals along the way.

---

### Post by SmarterThanMyPhone on 2009-12-21
bump.

I've read all the man pages for ping and didn't see anything pertaining to what I need. Not being able to monitor a running ping seems like a pretty serious omission from a networking standpoint. I cant believe its not here, surely I'm just not finding the hot key. 
I search on.

---

### Post by doas777 on 2009-12-21
fraid your going to have to write a script for that.

---

### Post by SmarterThanMyPhone on 2009-12-21
not my strong suite lol, I was hoping that wasn't gonna be the case. I do have a friend that a linux developer, I'll pester him some and see what that gets me.

---

### Post by lukeiamyourfather on 2009-12-21
The ping command is very primitive and meant for initial troubleshooting. If you want a more robust tool there are hundreds of others out there, they're just not called ping.

---

### Post by cgb on 2009-12-21
not entirely sure what you are trying to accomplish but if you want to just keep a recording of the ping stats over a given period of time you could pipe the output to a text file with possibly a similar code as below.  -i is the interval which you may want to change around as well as the -c which is the amount of pings to send.  The below code would basically run for 1 hour pinging every 10 seconds and outputting in the txt file.  You can pull the output then whenever you want by typing cat pingOutput.txt and it will show you the current results.   

```
ping -i10 -c360  www.google.com >> pingOutput.txt &
```

---

### Post by SmarterThanMyPhone on 2009-12-22
> **cgb said:**
> not entirely sure what you are trying to accomplish 

```
ping -i10 -c360  www.google.com >> pingOutput.txt &
```

Thats what I'm currently using and is close to what I'm after. In windows;
ping -t [www.google.com](www.google.com)
runs a ping until you stop it with ctrl-c. Now lets say that the pings are flying and I want the stats of the ping so far, but dont want the rest of the pings to stop. In windows I can press ctrl-break and get the current stats and the ping keeps running, it doesnt stop. I dont really know how to explain it beyond that, you might just have to try it to see what I'm talking about, any network admin knows what this is, its not a common ping command I guess.


> **lukeiamyourfather said:**
> there are hundreds of others out there, they're just not called ping.
and your preference/suggestion is?

---

### Post by SmarterThanMyPhone on 2009-12-22
> **lukeiamyourfather said:**
> The ping command is very primitive and meant for initial troubleshooting. 

I seriously disagree, I use extended ping commands in windows/linux/cisco ios on a daily basis for what can be very extensive troubleshooting, I dont see ping as primitive at all. 

Now if your a home user, not an admin ok maybe, but thats still just a maybe.

---

### Post by SmarterThanMyPhone on 2009-12-22
well someone over at yahoo answers got something for me, check this out.

Yeah.. CTRL break stops the script like Ctrl +C in Linux. Neither leaves the script running as far as I know.

If you want to ping something constantly and then only check in on it when you feel the need to see that stats.... Hm.... Um... Okay.. okay.. here we go.

#> sudo su
(password)

#> nano /usr/bin/isup 
(((PASTE THE FOLLOWING:)))
#! /bin/bash
# isup pings a given host once every 30 seconds then drops
# the info that can be read at will.
# Grab the line
#
if [ $# -eq 0 ];then
echo "usage: isup <hostname or ip>"
exit 0
else
THEHOST="$1"
. /usr/bin/isup.go
fi
##### END OF FILE
(quit and save ctrl + X, yes enter)

#> nano /usr/bin/isup.go
#((( PASTE THE FOLLOWING )))
function RUNIT () {
ping -c1 "$THEHOST" >> /usr/bin/isup.log
sleep 30
RUNIT
}
RUNIT &
#### END OF FILE
( save and quit)

#> nano /usr/bin/isread
#((( PASTE THE FOLLOWING:)))

#! /bin/bash
cat /usr/bin/isup.log | less
#### END OF FILE
(quit and save)

#> touch /usr/bin/isup.log
#> chmod 755 /usr/bin/isup*
#> chmod 777 /usr/bin/isup.log # could probably use 666

Okay ...
so now you have a PRIMATIVE program that once invoked pings a server once every 30 seconds in the background and pipes the results to a file which can be read at any time. 
USAGE:
#> isup [www.google.com](www.google.com) # start it
#> isread # read it
to stop it, you will need to:
#> ps aux | grep isup
then
#> kill <pid of isup>

That'll do but its a kludge...



Now even though I'm still testing this, I'd still like to see the hundreds of utils that make ping primitive, or at least a partial list.

---

### Post by SmarterThanMyPhone on 2009-12-22
mtr seems to be as close as I'm gonna get without writing a script myself. Convincing our director to let me run a linux box at work in place of my windows machine just got slightly harder lol.

---

### Post by lukeiamyourfather on 2009-12-22
Its by no means comprehensive but Stanford has put together a handy collection of links for network monitoring tools of all varieties (some are for Windows too).

[http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html](http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html)

As you've already seen a simple shell script (or Python script) can go a long way if you want to enhance an existing command. I used primitive to describe ping because it is relatively speaking. Not trying to downplay the usefulness of the command, just saying there are more robust tools out there too if ping doesn't do everything you want it to do.

---

