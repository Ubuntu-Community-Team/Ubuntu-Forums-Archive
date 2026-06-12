---
title: "Secure Copy issues."
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by Credo_78 on 2009-09-24
Hello all,

New to the forums here, and I'm hoping someone can help me out.  I'm having some odd issues with SCP.

I've got everything running properly on the server. I've configured, and set up the SSH server, I've added some entries to the /etc/hosts.equiv set up to allow certain connections using my particular login.

I've tested the copy by running the following command:
```

# scp test.txt mydomain:/home/usr

```here are the results:

```

user@domain's password: (entered password)

test.txt             100% |*****************************|    72       00:00

```which would indicate the file was successfully transferred, but when I look for the file in that particular directory, it's not there.  I've even searched the entire computer with no trace of the file being copied over...

what am I missing?  Why is it showing the transfer, but I can't find the file?  :confused:

Any help would be greatly appreciated!
Thank you very much in advance!

~C.

---

### Post by howlin_walleye on 2009-09-24
I'm not familiar with using hosts.equiv, and perhaps that's why your syntax looks a little odd to me. 

Normally, when I have sshd running on a server, I use ssh or scp from a remote machine like this:

ssh dan@server   (this assumes 'dan' is an account on the server). 

Similarly, I can copy a file to the 'dan' account on 'server' like this:

scp file.txt dan@server:/home/dan


In both cases, I am prompted for a password and all is well.  

Hope this helps, 
Dan

---

### Post by Credo_78 on 2009-09-24
That's basically what I've done.

scp test.text chris@server:/home/chris

I'm then prompted for a password, and the result is what I've shown:

```

test.txt             100% |*****************************|    72       00:00

```

But my point is that when I look in that directory, the file's not there!!! :(

---

### Post by scorp123 on 2009-09-24
Is "mydomain" really a hostname? I know it is only an example. That's now what I mean. I mean: is it really a hostname? Or are you by accident using something that isn't a proper hostname?

Then ... a few thoughts:

1.) hosts.equiv

By default OpenSSH ignores that file. Are you sure you configured the SSH server correctly? A guide Google just spit out:
[http://itg.chem.indiana.edu/inc/wiki/software/openssh/189.html](http://itg.chem.indiana.edu/inc/wiki/software/openssh/189.html)


2.) Does it work if you use IP addresses instead of hostnames?


3.) Enable verbose mode

```
scp -vvv file remoteuser@remotehost:/path/to/target/
```


4.) Did you check your local computer?

Sometimes if you have typos in your "scp" command line then the files end up on the local system, usually named in bizarre ways. Example: I want to transfer a file to my account "sysadm" on host "serenity" but because I am too tired I forget to type the path .... So I enter this command which won't work:
```
scp /path/to/source/file sysadm@serenity
```

Guess what happens ... the file ends up being copied into a file called "sysadm@serenity" on the originating host. 100% success. Not.

So ... maybe you have something similar? Could you please check if those files ended up on your local filesystem somehow?

---

### Post by scorp123 on 2009-09-24
> **Credo_78 said:**
>  But my point is that when I look in that directory, the file's not there!!! :( And you're really sure you're checking on the right host?  (you would be surprised how often it happens that people don't realise they're logged in somewhere else ... )

---

### Post by Credo_78 on 2009-09-24
> **scorp123 said:**
> And you're really sure you're checking on the right host?  (you would be surprised how often it happens that people don't realise they're logged in somewhere else ... )

To answer your first question: yes the host name is a correct one I can SSH to the host with no problem.  and I use that name for all my other sessions...

I have the machine I'm copying from open in a Putty session, and the remote server (the machine I'm copying to) open in another session. 

I run the RCP, then check my /home/chris directory on the actual server, and it's not there.

I've also done a find / -name "test.txt" on the target server with no results....

---

### Post by scorp123 on 2009-09-24
> **Credo_78 said:**
>  I run the RCP, then check my /home/chris directory on the actual server, and it's not there. and "scp -vvv ... " ?

---

### Post by Credo_78 on 2009-09-24
> **scorp123 said:**
> and "scp -vvv ... " ?

Stay tuned.  I'll let you know.

---

### Post by Credo_78 on 2009-09-24
No luck.

Here's the exact code I ran:

rcp -vvv test.txt [email]Chris@tripod.dlinkddns.com[/email]:/home/chris

it says the rile was successfully copied, but still nothing.  Grrrrrr!

---

### Post by scorp123 on 2009-09-24
> **Credo_78 said:**
>  rcp -vvv test.txt [email]Chris@tripod.dlinkddns.com[/email]:/home/chris  "rcp"?

Are you really using rcp ... or scp? And can I have the exact output please?

---

### Post by Credo_78 on 2009-09-24
Sorry, my mistake! I meant to say I'm running SCP - NOT rcp as I posted.

Here is a screen shot of the output of the copy results...

Let me know if you have any other questions!

[IMG]http://lh5.ggpht.com/_TwxrDGZpaLc/SrwHy5qpYqI/AAAAAAAAAG4/IlRhpDZaUa0/screenshot.jpg[/IMG]

---

### Post by Credo_78 on 2009-09-24
One other quick question...

if I'm in Putty connected to a computer (port 22), and I run the SCP command from within putty, does it not open the default SCP port (514), or does it go through port 22???? 

Depending on the answer, I may have found the solution...

---

### Post by scorp123 on 2009-09-25
> **Credo_78 said:**
> the default SCP port (514) scp was never ever on 514

And sorry to say so but that screenshot was useless. I wanted the full text output so I can read it from beginning to end.

---

