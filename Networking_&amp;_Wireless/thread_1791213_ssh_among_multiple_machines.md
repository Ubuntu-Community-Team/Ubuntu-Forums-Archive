---
title: "ssh among multiple machines"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by maclenin on 2011-06-26
Hello!

I would like to configure ssh so that I can ssh among multiple machines.

There are 4 machines at play - all are connected to my local network - and each has been assigned a unique ip.

desktop@ip0 (linux)
laptopA@ip1 (linux)
laptopB@ip2 (linux)
laptopC@ip3 (mac)


Is there a way to configure each of these machines so that they can all talk to any of the others - and play either client or host - depending on whose "sshing" whom?

Ultimately, I'd like to be able to ssh in a "similar" manner over lan, wan or internet.

Thanks for any thoughts!

[If google bears fruit, I'll report back....]

---

### Post by conradin on 2011-06-26
The simple answer is Yes.
However I'm going to assume I have no idea what it is exactly your trying to do, that it will involve automation, and that its some sort of parallel processing via ssh type deal. Is That right?

Can we get a bit more info about what you're trying to do?

For example:
I can ssh from here to my computer in Canada, to my computer on the 2nd floor to this computer. Why I would want to? IDK. I would inevitably have lags that I wouldn't have if I was just using my computer normally. Then Again, my employer thinks if they monitor the chat program, and its active that I must be working... So I can see some perks to what you're saying.

---

### Post by Toz on 2011-06-26
If I understand correctly, simply install the ssh server on each machine so that they can all accept incoming ssh requests.

_Using the GUI_: Startup "Ubuntu Software Centre", search for and install openssh-server.

_From the command line_: Startup the terminal emulator and type in:```
sudo apt-get install openssh-server
```

You might also want to install a front-end ssh gui app on each of the computers (if you prefer to use a gui to connect). Putty is a good product. Look for it in the software centre or: ```
sudo apt-get install putty
```

---

### Post by JRV on 2011-06-26
My solution is in post #13 in this thread:

[http://ubuntuforums.org/showthread.php?t=1674914&highlight=ssh&page=2](http://ubuntuforums.org/showthread.php?t=1674914&highlight=ssh&page=2)

you can also:```
nautilus sftp://USER@HOST/PATH/TO/FOLDER
```

---

### Post by maclenin on 2011-06-26
**conradin**!

Thanks for the encouraging "Yes"!

I think at this point, I am simply trying to get the pipes open - to be able to...```
ssh *@ip*
```...in any direction. Once I have those gates opened, I will then figure out what to do with it! Perhaps the most pressing need, at this point, is to be able to access the same "host" from any machine to allow automated/remote rsync back-ups.... I have the process configured from laptopA (client) to desktop (host) - but would like to get it up and running for the whole lot. I am sure other uses will evolve. 

...and **Toz**!

Thanks for your leads. I'll take a look at installing openssh-server, as you suggest.

Thanks, **JRV** - I've started looking into your solution, as well! 

Thanks, all, for your comments - arriving at a pace which left me no time to google!

I'll report back as I test!

---

### Post by maclenin on 2011-06-30
**Solved!**

Thanks, all!

(...in a nutshell...)

1. Installed both **openssh-client** and **openssh-server** - on all machines...
```
sudo aptitude install openssh-client openssh-server
```
2. Generated authentication keys (**id_rsa** and **id_rsa.pub**) - on all machines...
```
ssh-keygen
```
3. Passed along the public key (**id_rsa.pub**) from the **~/.ssh **directory of each machine (as intended client) to the ~/.ssh directories of every other machine (intended hosts/servers) - via email or ***scp** or usb... [*****With PasswordAuthentication set to yes (default) in **/etc/sshd_config** to allow for scp use during set-up and until keys in place - at which point I (re)set PasswordAuthentication to no - as the keys were now in charge.]
```
scp ~/.ssh/id_rsa.pub anothermachine@123.456.7.890:~/.ssh/
```
4. Created the single **authorized_keys** file for each host/server - within the .ssh directoy of each host/server - and added public keys of each new client with...
```
cat id_rsa.pub >> authorized_keys
```
5. Away we went!

**NB:** In my setting, each machine can act as either client or host/server, depending upon which is initiating the ssh request. Sender plays client - receiver plays host/server.... Each machine has, therefore, **authorized_keys** files, **id_rsa** (private keys), **id_rsa.pub** (public keys) and **known_hosts** files in their respective .ssh directories. I have also added separate **"client"** folders to the .ssh directories to house the public key file (**id_rsa.pub**) for each client - to help everyone keep track of her keys.

**NB2:** I also created a separate user-level **config** file (at [another's]("http://principialabs.com/beginning-ssh-on-ubuntu/") suggestion)  within ~/.shh to define access "short-cuts" - i.e. **user1@123.456.7.890** becomes **user1** - so a simple ssh request can be constructed as follows:```
ssh -X user1
```

Thanks, again, for setting me straight!

P.S. Have yet to attack the Mac....

---

