---
title: "SSH without receiving output"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by MKdx on 2009-06-18
Hey all,

I'm trying to use my pda to do some tasks on my main machine, but due to the pda limitations (screensize/ram...) it's not possible to execute some commands.

In ssh connection; is there a way to send a command to the host machine without receving the output in the guest machine? In other words, is there a way to execute some command on the host machine and have the output there not on the guest?

I just managed to connect them using ssh, and I'm trying to see how much I can push it before I reach the limit.

---

### Post by Cacadril on 2009-06-18
I suppose that "the guest" is the local machine where you are sitting at the keyboard, and the "host machine" is the remote machine to which you are connecting through ssh. (Standard terminology is "remote host" and "local host". A host is a computer that accepts (e.g.) logins, and the guest is you, who is logging in.)

If all you want is to suppress output to the terminal, try appending ">/dev/null 2>&1" after the command. That is, instead of a command "cat /etc/passwd" which outputs some data on your screen, type "cat /etc/passwd >/dev/null 2>&1" and hit enter.

The ">/dev/null" part sends the command's "standard output" to the device "/dev/null" (which simply discards all data).
The "2>&1" part sends the command's "standard error" data to the same place as the "standard output" is going.

But you also say "have the output there". Do you mean that the output should be shown on some screen connected to the remote machine? Or should the output be saved to a file? Or do you just want to have no output on your local screen? In the latter case, /dev/null is your friend. If you want a file, type a file name instead of /dev/null. If you want the data to appear on a remote screen, it is a bit harder. If you know about a terminal window on that screen, it is probably accessible by some name like /dev/pts/3 or /dev/tty2, it depends and it is a bit long to explain. You also would need "write permission" on the terminal window. Perhaps you first have to run a preliminary command that sets up a terminal window on that screen.

But in all these cases, your local terminal window will hang waiting for the command to finish. If you close the local window or the ssh connection before the command has finished, the command running on the remote machine will receive a "hangup signal" and stop running. If you want the command to keep running on the remote after you disconnect, you need to write "nohup" in front of the actual command, and add "&" at the end, like this:

  nohup cat /etc/passwd >/dev/null 2>&1 &

I hope this helps

---

### Post by MKdx on 2009-06-19
Perfect, it works now. Thanks Cacadril.

Yes, I meant the third case (terminal on remote screen), but you provided enough clues to know where to start.

---

