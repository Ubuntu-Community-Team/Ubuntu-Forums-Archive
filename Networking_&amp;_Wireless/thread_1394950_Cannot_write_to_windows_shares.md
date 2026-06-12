---
title: "Cannot write to windows shares"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by nylle on 2010-01-31
Hi,

I've recently switched to Ubuntu from debian, and I'm now running a fresh install of 9.04 32 bit. I have a Windows XP media computer which I would like to be able to browse using smb://. This worked fine on my debian system, but I cannot get it to work on ubuntu.

The windows XP machine has a couple of shares, e.g Music. I can access the Music share via smb://, but I cannot write to it. Nautilus just says "Permission denied". I can also see the default shares, e.g. E$, but if I try to open them I am prompted with a password, but no matter what I enter it seems to have no effect.

Any thoughts on how to proceed?

//Andreas

---

### Post by dlabelle11 on 2010-01-31
I'm having basically the same problem but with 9.10 and I get the prompt for the impossible password as soon as I try to open the computer.

I think the problem might be as simple as the net work not refreshing properly maybee getting some ip's messed up.

but Im also having problems at the command prompt with my su password

---

### Post by dlabelle11 on 2010-01-31
> **shill88 said:**
> Solved the problem by removing Windows live sign in assistant per the following [Post]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527"). Hope this helps others with the same problem.

Im going to try this

---

### Post by Iowan on 2010-01-31
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") are a few more things that may help.

---

### Post by Morbius1 on 2010-01-31
Some of the usual suspects for this sort of thing are:

See if "**encrypt passwords = No**" is in smb.conf. If it is put a # sign in front of the line.

It could be the ntlmv2 issue, although I think this only came up with Vista and Win7. Add the following line in the [COLOR=Blue][global][/COLOR] section of smb.conf:

```
client ntlmv2 auth = yes
```Try these two things first, and restart samba: [B]sudo service samba restart

[/B]I realize that samba is a server application and that the problem here is that a client is having problems accessing another server but there are parameters in smb.conf that also control the client.

---

### Post by nylle on 2010-02-06
Hi,

Sorry for dropping out for a week, work was extremely time consuming during the week. Thanks for your replies.

**Iowan:** I did look through that thread, but the problems described in that thread seem not to be directly related to the problems I have.

**Morbius1:** I tried both settings, but no change.

I can mount the shares statically through fstab, but the problem is that the machine is not always on, so I would prefer to only dynamically browse it.

BR/Andreas

---

### Post by headvampyre@hotmail.co.uk on 2010-02-06
hi 
first make sure that the shares are writeable and change the domain to the xp media machines name
that should work

---

### Post by Morbius1 on 2010-02-06
> **nylle said:**
> I can mount the shares statically through fstab, but the problem is that the machine is not always on, so I would prefer to only dynamically browse it.

You lost me here. If you add an entry in fstab to mount them then you have no issues ( assuming the server is up ). But if you browse then mount you do?

---

### Post by nylle on 2010-02-06
> **Morbius1 said:**
> You lost me here. If you add an entry in fstab to mount them then you have no issues ( assuming the server is up ). But if you browse then mount you do?

Yes, if I add the share to fstab, then I can mount it normally. The problem is using the smb:// to browse the shares. Trying to access the default shares (e.g. E$) results in the popup asking for username/domain/password where it doesn't seem that it matters what I put in.

I can access to shares that I've explicitly shared from the XP machine, but I can only browse the root level of those shares, and trying to write to them results in a permissions error.

//Andreas

---

