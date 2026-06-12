---
title: "W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by seedainvisible737 on 2007-04-26
Every time i perform a manual check for updates i get this error.

W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I am not even sure if I use Medibuntu. How do i stop it. 
they started to happen when I was downloading many pgms to play my dvds. at that time was having problems.

:-k
thanks

---

### Post by dreadlord_chris on 2007-04-26
> **seedainvisible737 said:**
> Every time i perform a manual check for updates i get this error.

W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I am not even sure if I use Medibuntu. How do i stop it. 
they started to happen when I was downloading many pgms to play my dvds. at that time was having problems.

:-k
thanks

That's telling you that you don't have the GPG key for that repository. This won't prevent you from downloading packages from there - it'll just prevent you from being able to verify that the packages you grab from there haven't been altered in any way.

You can do one of two things to fix this. If you want to keep using that repository you will want to import the GPG key (make sure that Synaptic/Adept is not open):
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```
After this you shouldn't get that error any more.

Or else just remove that repository from your list....

---

### Post by seedainvisible737 on 2007-04-30
ok, how do i remove it from my repository list?  is that in the synaptic package manager?

---

### Post by dreadlord_chris on 2007-05-01
> **seedainvisible737 said:**
> ok, how do i remove it from my repository list?  is that in the synaptic package manager?
Yup.... Settings > Repositories

---

### Post by seedainvisible737 on 2007-06-05
Hey!!! It worked.  No more erros.  I took the simple route removed it from my repository list.   

jthanks.

---

