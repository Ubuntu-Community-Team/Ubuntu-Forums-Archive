---
title: "Keep multiple processes alive. SSH. Bash script."
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by tfuglsang on 2012-07-19
Hello

Im trying to measure bandwidth, packet loss, latency and jitter between two computers on a wireless 802.11s mesh connection.

Im trying to make a (my first) bash script that can do the following:

1. SSH to another computer and start logging data from services (ptpd, tcpdump, iperf).
2. Start the same processes on my own computer and start logging data.
3. Once the iperf transmission on my own computer is finished, it should SSH into the remote computer and kill the the services.

The idea is for this these three steps run in a for-loop, that increases the package size transmitted by iperf for each iteration and logs the resulting data.

I know how to start a process on the remote pc by "ssh host@adress process".

I am however clueless on how to start multiple processes through SSH and logout without killing the processes, since the processes are terminated once I logout. I have looked at the "screen" and "nohup" commands, but dont know how to use them in a script.

Thanks in advance!

---

### Post by papibe on 2012-07-19
Hi tfuglsang. Welcome to the forums ):P

'screen' is very easy to use. Install it on the remote server and leave things running there. Take a look at this basic [steps]("http://ubuntuforums.org/showpost.php?p=11973829&postcount=3").

I hope it help, and let us know how it goes.
Regards.

---

### Post by tfuglsang on 2012-07-19
Thanks!

I found a solution to my problem (or at least some of it). Ill just post it here in case anybody have the same problem.

I used this guide: [http://www.pantz.org/software/ssh/using_ssh_and_sudo_instead_of_root_for_remote_commands.html](http://www.pantz.org/software/ssh/using_ssh_and_sudo_instead_of_root_for_remote_commands.html)

Together with the ```
nohup
``` command.

So I now call a script on my main computer with the line:

```
ssh host@adress 'echo password | sudo -S nohub ./dostuff.sh > /dev/null 2>&1 &'
```

This starts the 'dostuff.sh' script on the remote pc as sudo.

---

