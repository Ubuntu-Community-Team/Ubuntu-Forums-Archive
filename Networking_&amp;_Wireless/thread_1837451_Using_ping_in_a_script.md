---
title: "Using ping in a script"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by MG2R on 2011-09-01
Hi,

I'm trying to write a script that pings for a specific IP-adress. If the pinged host is available, the script should execute a command, if not it should execute a different command. This script should run every 15 minutes or so.

after some quick googleing I found this:
PING_OUT=`ping -c "$NB_OF_PING" -q "$IP_ADDR"`
min=`echo "$PING_OUT" | awk -F"/" '{print $4}'`
avg=`echo "$PING_OUT" | awk -F"/" '{print $5}'`
max=`echo "$PING_OUT" | awk -F"/" '{print $6}'`
mdv=`echo "$PING_OUT" | awk -F"/" '{print $7}'`

I'm not quite sure how I can implement this in a script that suits my needs (I'm a beginner at this).

Can anyone help?
Thanks!

---

### Post by sisco311 on 2011-09-01
I'm not sure if this is the best way to check if the host is available, but you can try something like:
```
if ping -c 5 IP-or-hostname > /dev/null 2>&1
then
    do somethin
else
    something else
fi

```

---

### Post by MG2R on 2011-09-01
Great, now I just need to figure out the repetition.

Thanks a lot so far!

---

### Post by sisco311 on 2011-09-01
> **MG2R said:**
> Great, now I just need to figure out the repetition.

Thanks a lot so far!

use a loop:
```

while true
do
    do something
    sleep 15m
done
```

---

### Post by MG2R on 2011-09-01
You're awesome! thanks a lot :)

---

### Post by sisco311 on 2011-09-01
> **MG2R said:**
> You're awesome! thanks a lot :)

You know what? You don't have to use ping. If your command fails, then most likely the host is not available:
```


while true
do
    if yourcommand [ARGS]
    then
        echo 'OKAY'
    else
        echo 'an error occurred: is host down?' 
    fi
    sleep 15m
done

```

---

### Post by MG2R on 2011-09-01
> **sisco311 said:**
> You know what? You don't have to use ping. If your command fails, then most likely the host is not available:
```


while true
do
    if yourcommand [ARGS]
    then
        echo 'OKAY'
    else
        echo 'an error occurred: is host down?' 
    fi
    sleep 15m
done

```

Yeah, that'd work if my command involved the host. What I'm trying to do is testing if my laptop is powered on and connected to the network to determine if the hard drives in my self-built NAS need to spin up or not.

Anyways, it worked up until I was trying to limit the amount of echo's, now it says there is a syntax error on line 8 :s
```
while true
do
    if ping -c 1 192.168.1.150 > /dev/null 2>&1
    then
        sudo hdparm -S 0 /dev/sda /dev/sdb
        if $last=1
            echo "RAID stand-by disabled"
        fi
        last=0
    else
        sudo hdparm -S 2 /dev/sda/dev/sdb
        if $last=0        
            echo "RAID stand-by enabled"
        fi
        last=1
    fi
    sleep 5s
done
```

---

### Post by sisco311 on 2011-09-01
The syntax of if is:

if <COMMANDS>; then <COMMANDS>; fi 
See:
[http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause](http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause)
and
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

```
if ((last == 1))
then
...
```

---

### Post by MG2R on 2011-09-01
> **sisco311 said:**
> The syntax of if is:

if <COMMANDS>; then <COMMANDS>; fi 
See:
[http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause](http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause)
and
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

```
if ((last == 1))
then
...
```

Still gives a syntax error:

line 9: syntax error near unexpected token 'fi'
line 9: '        fi'

```
available=0
while true
do
    if ping -c 1 192.168.1.150 > /dev/null 2>&1
    then
        sudo hdparm -S 2 /dev/sda /dev/sdb
        if ($available==1)
            echo "RAID stand-by disabled"
        fi
        available=0
    else
        sudo hdparm -S 0 /dev/sda/dev/sdb
        if ($available==0)        
            echo "RAID stand-by enabled"
        fi
        available=1
    fi
    sleep 5s
done
```

---

### Post by sisco311 on 2011-09-01
```
available=0
while true
do
    if ping -c 1 192.168.1.150 > /dev/null 2>&1
    then
        sudo hdparm -S 2 /dev/sda /dev/sdb
        if ((available==1))
        **then**
            echo "RAID stand-by disabled"
        fi
        available=0
    else
        sudo hdparm -S 0 /dev/sda/dev/sdb
        if ((available==0))
        **then**        
            echo "RAID stand-by enabled"
        fi
        available=1
    fi
    sleep 5s
done
```

((...)) is an arithmetic command, which returns an exit status of 0 if the expression is nonzero, or 1 if the expression is zero. Also used as a synonym for "let", if side effects (assignments) are needed. See: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression).

---

### Post by MG2R on 2011-09-01
> **sisco311 said:**
> ((...)) is an arithmetic command, which returns an exit status of 0 if the expression is nonzero, or 1 if the expression is zero. Also used as a synonym for "let", if side effects (assignments) are needed. See: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression).

Thanks! But I'm still getting the same eroor... Frustrating :/

---

### Post by sisco311 on 2011-09-01
> **MG2R said:**
> Thanks! But I'm still getting the same eroor... Frustrating :/

Sorry, I missed the absence of **then**

I edited my earlier post.

---

### Post by MG2R on 2011-09-01
> **sisco311 said:**
> Sorry, I missed the absence of **then**

I edited my earlier post.

Yeah, I just saw it myself :D
Thanks a lot!
Just to show the completed script:
```
enabled=2
while true
do
    if ping -c 1 192.168.1.150 > /dev/null 2>&1
    then
        if ((enabled!=0))
        then
        sudo hdparm -S 0 /dev/sda /dev/sdb
            echo "RAID stand-by disabled"
        fi
        enabled=0
    else
        if ((enabled!=1))
        then
        sudo hdparm -S 2 /dev/sda /dev/sdb
            echo "RAID stand-by enabled"
        fi
        enabled=1
    fi
    sleep 1m
done
```Works like a charm :)

---

### Post by sisco311 on 2011-09-01
> **MG2R said:**
> 
Works like a charm :)

Cool!

Don't forget to mark this thread as [SOLVED]! Thanks.

---

