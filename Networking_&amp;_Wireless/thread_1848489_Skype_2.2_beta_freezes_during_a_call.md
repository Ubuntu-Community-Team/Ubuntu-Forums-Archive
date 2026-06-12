---
title: "Skype 2.2 beta: freezes during a call"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by astrobob.tk on 2011-09-22
Hello,

I've been using Skype for quite some time recently & it was all going well.

Two days ago though, I was having a call & suddenly the call is interrupted; I thought it was a connection problem at the other end  (the other user) since I could see other contacts online. Not till after a while that I realized that Skype it self has freezed. It was not responding.

I quit Skype (ctrl+Q as usual) but i got a force quit message. I forced it & tried re-launching it. When it did it gave me a message that another instance of skype is on (see attachment). Anyhow, I killed the process & launched it again, but, same situation.

I tried a complete remove from synaptic & a reinstallation. I made the test call & it was fine. Then 2night i was making the same call; it worked for a few minutes & then the same issue came again.

I tried searching for a solution here on the forums & on the great search engine but couldnt find any relevant solution (maybe i missed something?)!

Is it only me who's facing such a problem ?

Configuration: 1st line in my signature

thanks in advance

---

### Post by papibe on 2011-09-22
When that happens it means that there's still a Skype process running in the background, probably 'half dead', hang or frozen.

To stop it, you will need to use the terminal. First Quit the Skype application. Then to check what other skype process are running try this:
```
$ ps aux | grep -i skype
```
If there's a skype program running in your system you'll see something like this:
```
pablo     **[COLOR="Red"]5128[/COLOR]** 58.2  1.6 264224 67228 ?        Sl   15:23   0:04 **[COLOR="Red"]skype[/COLOR]**
pablo     5172  0.0  0.0   3324   856 pts/2    S+   15:23   0:00 grep --color=auto -i skype
```
I marked red the important data. If there's a 'ghost' skype running, stop it like this:
```
$ kill -9 5128
```
Check again if the process is running. When you are sure there's no skype running, open again the application.

Hope this helps,
Regards.

---

### Post by Hakunka-Matata on 2011-09-22
you can also open **System Monitor**, choose processes, sort on name column, find multiple skype instances, and kill a couple.  Happens all the time to me, sometimes the blue skype icon disappears from the top panel, but Skype is still running, so you open a second instance, and wham, problem.

---

### Post by astrobob.tk on 2011-09-22
> **Hakunka-Matata said:**
> you can also open **System Monitor**, choose processes, sort on name column, find multiple skype instances, and kill a couple.  Happens all the time to me, sometimes the blue skype icon disappears from the top panel, but Skype is still running, so you open a second instance, and wham, problem.

> **papibe said:**
> When that happens it means that there's still a Skype process running in the background, probably 'half dead', hang or frozen.

To stop it, you will need to use the terminal. First Quit the Skype application. Then to check what other skype process are running try this:
```
$ ps aux | grep -i skype
```
If there's a skype program running in your system you'll see something like this:
```
pablo     **[COLOR="Red"]5128[/COLOR]** 58.2  1.6 264224 67228 ?        Sl   15:23   0:04 **[COLOR="Red"]skype[/COLOR]**
pablo     5172  0.0  0.0   3324   856 pts/2    S+   15:23   0:00 grep --color=auto -i skype
```
I marked red the important data. If there's a 'ghost' skype running, stop it like this:
```
$ kill -9 5128
```
Check again if the process is running. When you are sure there's no skype running, open again the application.

Hope this helps,
Regards.

I just used the System monitor to kill 2 process of skype.

After that I used the command u mentioned (after killing the 2 processes in the system monitor) & got:

```
$ ps aux | grep -i skype
astrobob  2062  0.0  0.0   3324   864 pts/4    R+   00:55   0:00 grep --color=auto -i skype

```

After that, I tried to launch skype (w/o killing this process) & it did launch & i was able to sign in.

I got the following while running skype:
```
$ ps aux | grep -i skype
astrobob  2471 38.0  1.8 260292 75732 ?        Sl   00:55   0:03 skype
astrobob  2666  0.0  0.0   3328   900 pts/4    S+   00:56   0:00 grep --color=auto -i skype

```

Then I quit skype (ctrl+Q) & rerun the same command to get:
```
$ ps aux | grep -i skype
astrobob  2818  0.0  0.0   3324   864 pts/4    S+   00:56   0:00 grep --color=auto -i skype

```

the last result keeps changing its id ?!

Though Skype is working again w/o displaying this "other instance", the problem is that Skype froze in the first palce. Why did that happen ?

I will attempt to launch skype from the terminal everytime i want to use it in case i get some useful info.

One morething: isn't there an alpha version ? where can i get it ? & why is Skype always in a beta for linux ?!

thanks

---

### Post by astrobob.tk on 2011-09-28
Hey again,

Skype is freezing everytime i make or receive a call :(

Chatting i fine; it works

would any log hep figure why skype is doing this ? or what is causing it ?

please help!!!

---

### Post by astrobob.tk on 2011-09-28
> **astrobob.tk said:**
> Hey again,

Skype is freezing everytime i make or receive a call :(

Chatting i fine; it works

would any log hep figure why skype is doing this ? or what is causing it ?

please help!!!

checking the System  Log view, i found the following:

```
process `skype' is using obsolete setsockopt SO_BSDCOMPAT
```

moreover, just now Empathy started crashing. I check dmesg & here's what I found:

```
empathy[24848]: segfault at 0 ip b59a9fe0 sp bfb8043c error 4 in libc-2.11.1.so[b58c9000+153000]
```

---

### Post by PayPaul on 2011-10-18
I had a related problem running Samba configurations. The thing just stalled on me. After trying several kill commands I hit upon the idea of using Sudo in front of it. Works every time apparently.

```
paulw@ubuntu:~$ sudo killall -9 smbd
[sudo] password for paulw: 
paulw@ubuntu:~$ $ ps aux | grep -i Samba
$: command not found
paulw@ubuntu:~$ ps aux | grep -i samba
root      7500  0.0  0.0 102992  3192 ?        Ss   18:13   0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- system-config-samba
root      7503  0.1  0.6 289628 26960 ?        S    18:13   0:02 /usr/bin/python /usr/sbin/system-config-samba
paulw     8277  0.0  0.0  13124   952 pts/0    R+   18:43   0:00 grep --color=auto -i samba
paulw@ubuntu:~$ kill -9 7500
bash: kill: (7500) - Operation not permitted
paulw@ubuntu:~$ kill 7500
bash: kill: (7500) - Operation not permitted
paulw@ubuntu:~$ kill 8277
bash: kill: (8277) - No such process
paulw@ubuntu:~$ kill -9 8277
bash: kill: (8277) - No such process
paulw@ubuntu:~$ kill 7503
bash: kill: (7503) - Operation not permitted
paulw@ubuntu:~$ sudo kill 7500

```Apparently some programs like Samba work in Root. I wonder if Skype does as well. That was the key phrase that made me think that Sudo was the only way to go. I'd love to know why Samba was stalling like that. For that matter what makes any program/package stall unexpectedly? How do I access and see the System Log?

This most recent business with a stalled program and the use of the right commands in terminal makes me all the gladder for using Ubuntu. At least i do have some measure of control over misbehaving programs. It does require a little research but I've much better luck solving these problems than I ever did with Windows.

---

### Post by astrobob.tk on 2011-10-21
> **PayPaul said:**
> I had a related problem running Samba configurations. The thing just stalled on me. After trying several kill commands I hit upon the idea of using Sudo in front of it. Works every time apparently.

```
paulw@ubuntu:~$ sudo killall -9 smbd
[sudo] password for paulw: 
paulw@ubuntu:~$ $ ps aux | grep -i Samba
$: command not found
paulw@ubuntu:~$ ps aux | grep -i samba
root      7500  0.0  0.0 102992  3192 ?        Ss   18:13   0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- system-config-samba
root      7503  0.1  0.6 289628 26960 ?        S    18:13   0:02 /usr/bin/python /usr/sbin/system-config-samba
paulw     8277  0.0  0.0  13124   952 pts/0    R+   18:43   0:00 grep --color=auto -i samba
paulw@ubuntu:~$ kill -9 7500
bash: kill: (7500) - Operation not permitted
paulw@ubuntu:~$ kill 7500
bash: kill: (7500) - Operation not permitted
paulw@ubuntu:~$ kill 8277
bash: kill: (8277) - No such process
paulw@ubuntu:~$ kill -9 8277
bash: kill: (8277) - No such process
paulw@ubuntu:~$ kill 7503
bash: kill: (7503) - Operation not permitted
paulw@ubuntu:~$ sudo kill 7500

```Apparently some programs like Samba work in Root. I wonder if Skype does as well. That was the key phrase that made me think that Sudo was the only way to go. I'd love to know why Samba was stalling like that. For that matter what makes any program/package stall unexpectedly? How do I access and see the System Log?

This most recent business with a stalled program and the use of the right commands in terminal makes me all the gladder for using Ubuntu. At least i do have some measure of control over misbehaving programs. It does require a little research but I've much better luck solving these problems than I ever did with Windows.


Well I didn't quite understand what you mean. Could you please expand on this ?

As for your question regarding the system log; you can use the command "dmesg" for kernel related messages & using the System > Administration > Log file viewer.

Hope this helps.

---

