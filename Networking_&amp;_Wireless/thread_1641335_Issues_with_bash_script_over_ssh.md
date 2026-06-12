---
title: "Issues with bash script over ssh"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by tr33m4n on 2010-12-08
Hello there,

I've been trying to set up guake to automatically open 2 programs in two different tabs via ssh on my remote server. I have succeeded in doing this, however whenever the last command is run the terminal tab locks up and i can't enter any input, the only command that works is ctrl+c to kill (in this case) iptraf.

I think it might be something to do with how i'm sending my ssh password using echo and pipe... can anyone help? this is my script:

```
#! /bin/bash
# script to launch multiple guake windows on Network21 local server
guake --rename-tab=Htop21 --execute-command="ssh -t 192.168.1.137 'htop'" &
sleep 5 &&
guake --new-tab=2 --rename-tab=Iptraf21 --execute-command="ssh -t 192.168.1.137 'echo password | sudo -S iptraf'" &
```

the first and second commands always work, whilst the last one loads iptraf then the cpu maxes out and i can't enter anything unless i kill the program. I've also tried nload and a couple of others, with the same results.

Cheers
Dan

---

### Post by tr33m4n on 2010-12-09
I've changed the echo line to
```
echo -e password\n
```

still not working properly :S

---

### Post by CharlesA on 2010-12-09
That's not the way to tell sudo what yer password is. It's "hung" cuz it's prompting for yer password in the background.

See [here]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo").

---

### Post by tr33m4n on 2010-12-09
Well it passes the password to sudo anyway because iptraf launches... however iptraf and any other program appear like its receiving many many key strokes and the cpu hits 100... this is the only way I can think of to pass my sudo password on the remote server

---

### Post by tr33m4n on 2010-12-09
Never mind, I've disabled sudo for my user...

---

### Post by CharlesA on 2010-12-09
> **tr33m4n said:**
> Never mind, I've disabled sudo for my user...

You can set it so that one program doesn't prompt for yer password if you use sudo with it.

Is that what you did?

---

### Post by tr33m4n on 2010-12-09
Yes, i set the following

%doyle ALL=(ALL) NOPASSWD: /bin/sh -c /usr/sbin/iptraf ""

Thanks for the help

---

