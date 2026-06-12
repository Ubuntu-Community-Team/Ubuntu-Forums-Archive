---
title: "bash script won't continue after ssh to a client"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2011-04-27
I have a script that ssh to a host. The problem is the next command in the script file doesn't run on the host. Seems that the script is exited after ssh to the host.

#!/bin/bash
ssh client1
ls

however the 'ls' command won't run on client1

---

### Post by Doug S on 2011-04-27
The ls command is not supposed to run on client1.
It will run on the original computer once you log out of the client1 ssh session.

---

### Post by mahmoodn on 2011-04-27
ok that is the problem. I want the 'ls' command run on client1.

---

### Post by Doug S on 2011-04-27
Execution of the script will not transfer to client1 upon successful ssh login.
However, you can specify a command to execute on client1 upon sucessful ssh login.
I.E. I think this would do what you want:
 
#!/bin/bash
ssh username@client1 ls
 
And "ls" could be replaced by a script name (the script would have to be located on client1) to execute more commands if desired.

---

### Post by fdrake on 2011-04-27
> **Doug S said:**
> Execution of the script will not transfer to client1 upon successful ssh login.
However, you can specify a command to execute on client1 upon sucessful ssh login.
I.E. I think this would do what you want:
 
#!/bin/bash
ssh username@client1 ls
 
And "ls" could be replaced by a script name (the script would have to be located on client1) to execute more commands if desired.

and also username@client1 should need the right to execute those command and to execute the file... basically a list of access problem..

---

### Post by mahmoodn on 2011-04-27
ok thanks. I got it

---

