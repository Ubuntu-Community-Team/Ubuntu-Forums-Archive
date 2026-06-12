---
title: "ssh agent forwarding issue from one host?"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by dkoleary on 2012-11-15
Hi;

I have a squirrelly issue with ssh agent forwarding and I'm out of ideas on how to troubleshoot it.

I have four systems:

* my laptop (dolaptop1) running ubuntu ver 11.1 which holds my private key and is the location of the running ssh-agent.
* a desktop (fw) running ubuntu ver 12.04
* Another desktop (samba) running fedora core 8
* A last desktop (chester) running fedora core 17

From my laptop, I can access all three desktops:

$ for h in chester fw samba
> do
> ssh ${h} hostname
> done
chester
fw
samba

From samba and chester, I can access the other two desktops:

# h
samba
# for h in fw chester
> do
> ssh ${h} hostname
> done
fw
chester


# hostname                                      
chester
# for h in fw samba
do
ssh ${h} hostname
done
fw
samba

From fw, I can't access anything:

# ssh samba hostame
Permission denied (publickey,gssapi-with-mic). # pwd authentication turned off

# ssh chester
root@chester's password: 

The ssh directory is locked down:
# ls -ld ~/.ssh
drwx------ 3 root root 4096 Nov 14 20:22 /root/.ssh/

ssh_config is set to forward the agent:

# grep -v -e ^# -e ^$ /etc/ssh/ssh_config which is the same as samba:

Host *
  ForwardAgent yes
  ForwardX11 yes

And the env has the right information for the agent:

# set | grep -i ssh
_=/etc/ssh/ssh_config
Pwd=/etc/ssh
PWD=/etc/ssh
SSH_AUTH_SOCK=/tmp/ssh-jvNKDF7642/agent.7642
SSH_CLIENT='192.168.12.51 34743 22'
SSH_CONNECTION='192.168.12.51 34743 192.168.12.1 22'
SSH_TTY=/dev/pts/1

I've compared the output of ssh -v -v from both the functional and nonfunctional systems.  The only thing out of the ordinary is:

debug1: Roaming not allowed by server

So far, google searches haven't given me much to check, though.

Does anyone have an idea on what's causing this and/or how to fix it?  I appreciate any info/hints/tips/suggestions.

Thanks.

Doug O'Leary

---

