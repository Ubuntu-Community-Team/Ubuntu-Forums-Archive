---
title: "how to run  ssh  shell command?"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by luofeiyu on 2011-05-10
command1:
ssh pt@192.168.1.101 ls
command2:
ssh pt@192.168.1.101 totem ~/t1
Cannot open display:
Run 'totem --help' to see a full list of available command line options.
command1 can run, command2 can not run,would you mind to tell me why?

---

### Post by YesWeCan on 2011-05-10
ssh is a console/text interface by default.
The output of 'ls' is just text to the console so this works.

If you try a command that requires an X window, like totem, then this will not work by default. The remote host will complain that it can not open an X window for the calling ssh client.

Instead you must add -X to the ssh command. You may also want to add -C to compress the data transfer and speed it up.
ssh -XC pt@192.168.1.101 totem ~/t1
and the /etc/ssh/sshd_config file on the remote host needs to say 'X11Forwarding yes'. If you have to change this, restart the sshd daemon 'sudo /etc/init.d/ssh restart'

Adding -v is useful as it gives you a verbose explanation of the connection events.

---

### Post by luofeiyu on 2011-05-10
A computer is pengtao(username) 192.168.100
B computer is pt(username) 192.168.101
in A console:
ssh -XC  -r sound:local pt@192.168.1.101 totem /home/pt/t1
(the command can't run
 ssh -XC  -r sound:local pt@192.168.1.101 totem ~/t1)
but there is another problem,no voice in my computer A!

it's so strange a thing
the video is on the  A  computer ,no voice; the voice is on the B computer ,no video!!

how can i get voice?

---

