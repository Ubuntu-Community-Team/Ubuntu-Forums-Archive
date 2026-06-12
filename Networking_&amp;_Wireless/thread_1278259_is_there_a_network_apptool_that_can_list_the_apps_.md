---
title: "is there a network app/tool that can list the apps that uses the network?"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by Anxious Nut on 2009-09-29
Is there a program/tool that monitors the upload/download and gives you a list of all the applications that is using the network?

thanks in advance,
AnxiousNut

---

### Post by eylisian on 2009-09-29
lsof might be what you need. It stands for list open files and will display a listing of files opened by processes. The -i switch is what you want for the network connections.

Using a terminal issue;

lsof -i

or (to list all and not just the current user connections)

sudo lsof -i

You can also inquire about specific ports

sudo lsof -i :22

Would list all SSH connections

Hope this helps.

---

### Post by eylisian on 2009-09-29
Apologies for not addressing the bit about monitoring your up/down. I'll sometimes use good old ifconfig and watch.

watch ifconfig eth0

Gives 2 sec updates and you can scope the RX/TX as bits are moving. I use Gkrellm on my desktop to monitor things, but it doesn't show network application connections.

---

### Post by MC_Claus on 2009-09-29
If you want another one try 
```
netstat
```

This gives you all the connections you have outbound, and the ports and so on.

```
netstat -l
```

Gives the ports you are listening on. I find it easy to use when I need to find out if ie Apache is listening on the right ports.

I'm not sure if it shows the traffic amount in kB/mB but it will give you a lot of info on your connections.

---

### Post by Anxious Nut on 2009-09-29
lsof -i seems fine, thanks eylisian

but if there is a more specific tool please tell me about it, yes this does tell me the programs that are using the netork like firefox, SSH, and thunderbird, but doesnt tell me if im using the terminal to download packages (apt-get). Im asking for this because sometimes i find my network indicator in the system monitor so high and i wonder what program is using the network. 

but this lsof -i is good, thanks again eylisian

---

