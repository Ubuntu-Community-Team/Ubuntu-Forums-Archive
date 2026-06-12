---
title: "How to send &quot;enter&quot; command to serial IR Blaster?!"
date: 2010-01-02
forum: Mythbuntu
---

### Post by tegwilym on 2010-01-02
I'm building a new Mythtv box and just about got the ugliest part of the thing working, yes, the infamous IR blaster to the DirecTV box to change the channels.

So, I'm almost there since when I watch TV I enter the new channel and hit  [enter] to change it.  I see that the computer IS sending the numbers since the DirecTV receiver shows the numbers change, but then it goes back to the original channel again.  It just need to send and "enter" or "ok" command to kick the new channel.  I just can't figure out where to put the code in the channel changing script.  Here is what I have that WILL send the channel, but needs to send enter.


```
#!/bin/sh

REMOTE_NAME=sat
cmd="$1"
case $cmd in
    [0-9]*)
    for digit in $(echo $1 | sed -e 's/./& /g'); do
        irsend SEND_ONCE $REMOTE_NAME $digit
        sleep 1
        #sleep 1
        # If things work OK with sleep 1, try this for faster channel changes:
        # sleep 0.3
    done
    ;;

    *)
        irsend SEND_ONCE $REMOTE_NAME $cmd
        ;;
esac
~                      

```

I do understand there is a fix for this where you put in some code similar to this: 
```

# Do we need to send enter
if ( $needs_enter )
{
system ("$rc_command SEND_ONCE $remote_name ENTER");
} 
```


....but I think I'm not sure where it goes in my code that I shared above.  Anyone know how I can send and "enter" command with this thing?  If that sends, then I can change my channels!

Thanks for any tips or advice.

Tom

---

### Post by tegwilym on 2010-01-02
Oh, I'm not totally new at this either.  My current box is a Mythdora 5 machine that I'm trying to migrate to the new Mythbuntu machine.  The Ir blaster was a challenge on that also, but much harder.   At least the Mythbuntu is sending numbers to the receiver!

I've been on Myth for about 2 years now and would never go back to normal TV - or ever touch any Microsoft media center thing.  yuck!
Tom

---

### Post by azmyth on 2010-01-02
I'd put it right after the done

done
        irsend SEND_ONCE $REMOTE_NAME enter

you need to make sure you change "enter" to the proper entry in your lircd.conf file for the transmitter. Probably enter, select, or ok.

---

### Post by tegwilym on 2010-01-03
> **azmyth said:**
> I'd put it right after the done

done
        irsend SEND_ONCE $REMOTE_NAME enter

you need to make sure you change "enter" to the proper entry in your lircd.conf file for the transmitter. Probably enter, select, or ok.

Thanks!  I'll give that a try and see what happens.  I didn't see "Enter" in the lircd.conf file, but there was "OK" so I'll use that code.

Thanks for the tip.  I'll see what happens!  :)

Tom

---

### Post by tegwilym on 2010-01-04
azmyth, 
Thanks a lot for the help.  Tried the line after the 'done' tried it out and it works perfectly now!  
More bonus points for the friendly and helpful Ubuntu community.  :)

...now on to tweaking the DVD sound.
Tom

---

