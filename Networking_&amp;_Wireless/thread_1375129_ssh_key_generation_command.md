---
title: "ssh key generation command"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by wbrady4927 on 2010-01-07
I want to run ssh-keygen -f [filename] but also specify no password. I know the -N option is used to specify the password but putting -N with nothing after it isn't permitted. All ideas are welcomed!

---

### Post by lewisforlife on 2010-01-08
> **wbrady4927 said:**
> I want to run ssh-keygen -f [filename] but also specify no password. I know the -N option is used to specify the password but putting -N with nothing after it isn't permitted. All ideas are welcomed!

```
ssh-keygen [filename] -t rsa
```

You will be prompted for a pass phrase, simply press enter without entering one and a pass phrase will not be set.

You might want to check out this page: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by wbrady4927 on 2010-01-08
I should have been more clear. I understand you can do that, but I want to do this without user input. It is a part of an installation script and I don't want to the person running it to have to press Enter. I just want it to know from the command. Thank you for your advice however.

---

### Post by lewisforlife on 2010-01-08
This is just a start:

```
ssh-keygen -f [filename] | yes ""
```

I believe this will achieve what you are looking for.  But yes runs forever until killed with ctrl+c, if you can find a way to automatically kill yes after a few seconds that would be ideal.

---

### Post by lewisforlife on 2010-01-08
I am not good with bash, but you could run a bash script that does this without prompting:

```
#!/bin/bash

ssh-keygen -f file | yes "" &
sleep 1
killall yes
exit
```

This will create the key pair and set the paraphrase to nothing.  There has to be a better way of doing this.  I am the king of figuring out round-about complicated ways of doing things. ;)

---

