---
title: "Bash script (or alias) using ssh &amp; notify-send"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-08-15
I have two computers on a LAN both using Jaunty.

I "administer" both computers and have passwordless ssh access to both systems. I'm trying to write a script (or an alias) so that I can send notification bubbles to the computers remotely. Issuing the command```
ssh -X user@host 'DISPLAY=:0 notify-send "TEST MESSAGE."'
```at a local terminal works like a charm - the notification bubble containing the message appears on the remote screen.

Since the text "TEST MESSAGE." is just an example used here, and the message I will want to send will vary every time, "TEST MESSAGE." has to be made into a variable. If I create an alias on each system, such as ```
alias chat='DISPLAY=:0 notify-send'
```I can log in remotely, and at the remote prompt, simply enter ```
chat "FOO BAR."
```and the quoted text, along with the quotes, is appended to the end of the aliased command.

In trying to create an alias or a script - let's name it 'chat' in either case - that resides locally but uses SSH to execute a remote command, setting the variable is proving to be quite a headache. Since the structure should be the same as the above example, I have to pass along the double quotes as input. In trying to do so, I keep getting errors such as, "Invalid number of options," or, "No summary specified."

In using an alias, structured like so ```
alias chat='ssh user@host DISPLAY=:0 notify-send'
```I can send messages to the remote computer and have them appear on screen, but only if they are one or two words long - three words produces the "Invalid number of options" error.

In using a script, I have to assign the "QUOTED MESSAGE" to a variable, otherwise I get the "No summary specified" error - the same error as if you went to a local prompt and typed ```
notify-send ""
```without any text between the quotes.

In trying to nest the variable inside those quotes, like this ```
ssh user@host DISPLAY=:0 notify-send "$1"
```again produces errors. Exchanging the $1 variable for $@ causes the error to switch from one to the other.

Can anyone offer me pointers as to how I would pass a quoted string as a variable into a simple one-liner like this?

---

### Post by ibuclaw on 2009-08-15
```
function chat { ssh -X user@host 'DISPLAY=:0 notify-send "$@"'; }
```

Give that a whirl.

Regards
Iain

---

### Post by detroit/zero on 2009-08-15
> **tinivole said:**
> ```
function chat { ssh -X user@host 'DISPLAY=:0 notify-send "$@"'; }
```Give that a whirl.

Regards
Iain
No go. The script executes without errors, but no message is displayed on the remote screen.

---

### Post by detroit/zero on 2009-08-15
The final, working copy:```
#!/bin/bash
#
#Send messages through SSH to remote hosts' notify-osd
#
message="$@"
ssh -X user@host "DISPLAY=:0 notify-send \"$message\""
exit
```I was close, I guess. Just had to get the quotes & escapes right.

---

### Post by irfannp on 2010-01-11
But running this script gives me error that command notify-send not found.

#!/bin/bash
#
#Send messages through SSH to remote hosts' notify-osd
#
message="$@"
ssh -X user@host "DISPLAY=:0 notify-send \"$message\""
exit

---

### Post by detroit/zero on 2010-01-11
So install it.
```
sudo apt-get install notify-send
```

---

### Post by Belizeian on 2010-01-11
E: Couldn't find package notify-send

---

### Post by detroit/zero on 2010-01-11
Ah, I see. The package has changed. notify-send is now provided by libnotify-bin.

A simple Google search would have told you as much.

---

### Post by mohave on 2010-02-22
Thanks Detroit/Zero very useful!

---

### Post by jamesisin on 2012-02-11
I keep seeing this solution come up but I am getting a dbus error when I try to run notify-send remotely.  I am trying to display the message on whichever user happens to be signed in.  Is that the problem?  Or is it something else?

```
ssh user@remote 'DISPLAY=:0 notify-send "HELLO" "Some stuff."'
```

---

### Post by merc82 on 2013-01-28
In my case I was able to get this working by changing the display number. I used the "w" command on the remote host to determine the display I wanted the notification to appear on. 

"w" reported ":1.0" so I used:
ssh user@remote-host "DISPLAY=:1.0 notify-send "Hello" "

---

