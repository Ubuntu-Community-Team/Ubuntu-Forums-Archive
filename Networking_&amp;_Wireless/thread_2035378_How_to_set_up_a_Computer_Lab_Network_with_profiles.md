---
title: "How to set up a Computer Lab Network with profiles"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by HugoCore on 2012-07-30
Hi all,

I need an advice to how set up a computer lab student network. 
The project is to setup a computer lab network with a client-service system and a directory service.
Now the main goals are:

- Manage users (username, passwords, permissions of what can do inside the client machine operating system) on the server
- Each user have their data/profile/files storage at the server
- Each user can logon at any computer client machine and load up their profile/data
- Distribute from the server, the client machine system operative (ubuntu), meaning that, the client machines have all the same operating system, programs and configurations. Per example, if a new program is necessary to exist in the client machines, do something in the server and propagate that addition to the client machines.

The scenario is very much a like, a student library or lab linux network system.

We have the hardware, with software and operating system you advice?

Best Regards

---

### Post by lukeiamyourfather on 2012-07-30
Start here, it will cover 99% of what you want.

[https://help.ubuntu.com/12.04/](https://help.ubuntu.com/12.04/)

To manage software on the systems there are a few ways. Ubuntu offers Landscape which is a commercial service. Also check out CFEngine.

[http://en.wikipedia.org/wiki/CFEngine](http://en.wikipedia.org/wiki/CFEngine)

---

### Post by HugoCore on 2012-07-30
> **lukeiamyourfather said:**
> Start here, it will cover 99% of what you want.

[https://help.ubuntu.com/12.04/](https://help.ubuntu.com/12.04/)

That's not very helpful. I ask for a advice not "go F1". Like software's, links or tutorials...

For what I've been searching and testing, NFS with NIS is a solution, but I find NIS very complicated and unsecure. Any advices for the system?

> **lukeiamyourfather said:**
> To manage software on the systems there are a few ways. Ubuntu offers Landscape which is a commercial service. Also check out CFEngine.

[http://en.wikipedia.org/wiki/CFEngine](http://en.wikipedia.org/wiki/CFEngine)

Thanks, I will check it out CFEngine or similar.

Isn't anyone who already set up a network like this? What you use?

---

### Post by Kirk Schnable on 2012-07-30
We are already doing this at work, and I had a huge hand in helping to implement it.

We use an Active Directory server to authenticate our users.  An open source alternative might do the trick, but I don't have any first-hand suggestions.

We use Likewise Open to authenticate users with Active Directory.

We do not synchronize student files. They're deleted upon reboot and users are told to put everything in Dropbox.  However, before our bosses told us to take this approach, I believe my coworker worked something out to connect to a Samba share and mount it at login.  This might be a solution to your question, but I am not sure he'd be able to find his configuration files again.  It would have allowed our students to use their synchronized My Documents folder across Windows and Linux machines on our network.

As far as distributing software, we use CloneZilla to image the computers.  After CloneZilla, I have Puppet installed on the image, which fires itself up and begins synchronizing applications, files, whatever you tell it to do.

Short version: Look at Likewise\PBIS-Open, CloneZilla, and Puppet Labs.

If you have any questions, which I'm sure you will, I will be subscribing to your thread.

Kirk

---

### Post by HugoCore on 2012-07-30
Thank's Kirk for your complete answer. That was the kind of answer that I was hoped to get it.

To have a Active Directory we will need a Windows Server right? We can't and I now see the need t buy a Windows Server now. That has to be an alternative.

The other issue is the synchronization. We really need to have the files synced, so that the users don't lose nothing.

Btw, what is the purpose of Puppet?

---

### Post by Kirk Schnable on 2012-07-30
> **HugoCore said:**
> Thank's Kirk for your complete answer. That was the kind of answer that I was hoped to get it.
No problem, glad I have an answer you like.

> **HugoCore said:**
> To have a Active Directory we will need a Windows Server right? We can't and I now see the need t buy a Windows Server now. That has to be an alternative.
Correct, as Active Directory is a Microsoft product.  We repurposed it, as we still have some Windows computers on our network.  It probably would not have been our choice for authentication if we'd done a Linux deployment from the ground up.

Check this out: [http://serverfault.com/questions/13419/what-are-some-good-open-source-alternatives-to-active-directory](http://serverfault.com/questions/13419/what-are-some-good-open-source-alternatives-to-active-directory)

> **HugoCore said:**
> The other issue is the synchronization. We really need to have the files synced, so that the users don't lose nothing.
I'll ask my coworker if he remembers how he had that setup with Samba.

> **HugoCore said:**
> Btw, what is the purpose of Puppet?
Puppet enforces a policy state on a computer.

It's capable of synchronizing files, changing file permissions and owners, and updating\installing packages from Apt.  Once installed, it runs at a specified interval (15 mins by default) and keeps the changes you asked enforced.

Check out the Puppet Types Reference for some sample code and some brainstorming fuel: [http://docs.puppetlabs.com/references/latest/type.html](http://docs.puppetlabs.com/references/latest/type.html)

In particular, read these sections carefully:
[http://docs.puppetlabs.com/references/latest/type.html#cron](http://docs.puppetlabs.com/references/latest/type.html#cron)
[http://docs.puppetlabs.com/references/latest/type.html#file](http://docs.puppetlabs.com/references/latest/type.html#file)
[http://docs.puppetlabs.com/references/latest/type.html#exec](http://docs.puppetlabs.com/references/latest/type.html#exec)
[http://docs.puppetlabs.com/references/latest/type.html#package](http://docs.puppetlabs.com/references/latest/type.html#package)

For your file sync\NFS idea, you might find this Puppet Type useful:
[http://docs.puppetlabs.com/references/latest/type.html#mount](http://docs.puppetlabs.com/references/latest/type.html#mount)

Hopefully that reading will spark some new questions and ideas toward your deployment.

Kirk

---

### Post by HugoCore on 2012-07-30
Thanks for the help Kirk.

From what I've seen, Samba can do the AC job. Manage the users and manage their profiles right?

With puppet or similar we could mount the profile on login from Samba, maybe?

Maybe most of my problems would be gone with Samba.

But, from what I've also seen, Samba it's more focused on Windows clients. Maybe there is a better alternative/solution?

---

### Post by Kirk Schnable on 2012-07-30
I doubt you'd want to use Puppet to mount individual users' home directories.  That's not how it's designed to be used.

What you'd want to do is mount a single share (NFS?) and then have properly defined permissions to keep users out of each others' files.  Then Puppet could mount that share.

Other than NFS, I'm not aware of anything that is really designed to do this.  My university computer lab has an NFS approach to home folders for their Mac lab.

You are correct that Samba is designed for Windows interaction, so using it on Linux is not preferred, but hey, it works.

Kirk

---

### Post by lukeiamyourfather on 2012-07-31
> **HugoCore said:**
> That's not very helpful. I ask for a advice not "go F1". Like software's, links or tutorials...

Your original post was asking a general question so you got a general answer. It still has the information you're looking for if you spend more than sixty seconds looking at it.

[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

---

### Post by Kirk Schnable on 2012-07-31
> **lukeiamyourfather said:**
> Your original post was asking a general question so you got a general answer. It still has the information you're looking for if you spend more than sixty seconds looking at it.

[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

I'd say the response given was an answer to the question "How do I use Ubuntu?".  The original poster's question was not *that* generic.

Kirk

---

### Post by lukeiamyourfather on 2012-08-01
> **Kirk Schnable said:**
> I'd say the response given was an answer to the question "How do I use Ubuntu?".  The original poster's question was not *that* generic.

Kirk

Really? Thanks for your opinion! :roll:

---

### Post by snowguy on 2012-08-07
HugoCore, I'm interested (and I'm sure others are as well) in how your experience goes. What you end up using, etc. Can you please post back here with that?

Also, I am wondering if you considered at all using LTSP? I don't use LTSP but it sounds like what you are looking for.

---

