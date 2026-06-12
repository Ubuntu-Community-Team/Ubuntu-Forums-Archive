---
title: "Update Manager Authorization Dialog Inconsistentcy"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by fatman65535 on 2010-09-22
In using Update manager in Karmic and Lucid; 
**_authorization is requested before the package cache information is updated_**. 

Once the package cache is updated, any new or updated packages are installed with any further authorization.

Now, in my testing of Maverick, 
**_you can update the package cache information with*OUT* authorization_**.

Once the package cache is updated; _you are required to obtain authorization **before** _any updates are installed. 

Notice carefully the change in behavior!

Karmic and Lucid - authorization [U]before updating the cache.
[/U]Maverick -  _authorization before installing the packages._

Now, I am NOT saying that one is right, and the other is wrong; but I am pointing out an inconsistency.  Perhaps this is a deliberate change, perhaps it is a screwup. perhaps, I am being too d----d picky, but, it is these ridiculous things that drive (l)users nuts. Unfortunately, I am part of the `help^Hl desk at work; and it would be nice to have a hand in ridding the world of such silly inconsistencies.

---

### Post by ranch hand on 2010-09-22
If you would bother to read you might nave gotten the information on that.

There are obvious warnings that this OS is a beta.  It does not work like a regular release, the repos are not handled like a regular release.

There is a prominent  Sticky on this.  Try reading, you might like it.

---

### Post by 23meg on 2010-09-22
> **ranch hand said:**
> If you would bother to read you might nave gotten the information on that.

There are obvious warnings that this OS is a beta.  It does not work like a regular release, the repos are not handled like a regular release.

There is a prominent  Sticky on this.  Try reading, you might like it.

This has nothing to do with Maverick being beta and not working like a stable release, and isn't covered in any stickies. You don't seem to have read the post thoroughly.

[QUOTE=fatman65535]
Now, I am NOT saying that one is right, and the other is wrong; but I am pointing out an inconsistency. Perhaps this is a deliberate change, perhaps it is a screwup. perhaps, I am being too d----d picky, but, it is these ridiculous things that drive (l)users nuts. Unfortunately, I am part of the `help^Hl desk at work; and it would be nice to have a hand in ridding the world of such silly inconsistencies.[/QUOTE]

This is due to Update Manager using the aptdaemon backend for installing packages in Maverick, as opposed to the Synaptic backend that it used to use earlier. Thanks to some PolicyKit magic, aptdaemon doesn't require you to authenticate to check for updates.

It is of course a deliberate change, and is overall an improvement over the old situation for various reasons. Such behavior isn't guaranteed to be absolutely consistent over Ubuntu releases; it's usually not possible to improve things without changing them around.

---

### Post by jpeddicord on 2010-09-22
> **mgunes said:**
> 
It is of course a deliberate change, and is overall an improvement over the old situation for various reasons. Such behavior isn't guaranteed to be absolutely consistent over Ubuntu releases; it's usually not possible to improve things without changing them around.

To add to this, this was the behavior in Lucid for some time before update-manager was switched back to the Synaptic backend. I like the new way of checking for updates since I don't need to type in my password just to *see* if there's something to do.

---

### Post by 23meg on 2010-09-22
> **jpeddicord said:**
> To add to this, this was the behavior in Lucid for some time before update-manager was switched back to the Synaptic backend. I like the new way of checking for updates since I don't need to type in my password just to *see* if there's something to do.

That was during the Karmic development cycle, not Lucid. aptdaemon wasn't deemed reliable enough at the time and the default backend was switched back to Synaptic.

And right now, the Synaptic backend will automatically be reverted to if aptdaemon isn't available. You can also choose to use the Synaptic backend with the UPDATE_MANAGER_FORCE_BACKEND_SYNAPTIC environment variable.

---

### Post by mc4man on 2010-09-22
> And right now, the Synaptic backend will automatically be reverted to if aptdaemon isn't available

I guess that a little progress has been made there, instead of update manager crashing before installing updates it will right after.

Probably better atm to kept aptdaemon for those that, for whatever the reason, don't want it installed.

---

### Post by fatman65535 on 2010-09-23
> **mgunes said:**
> This has nothing to do with Maverick being beta and not working like a stable release, and isn't covered in any stickies. You don't seem to have read the post thoroughly.



This is due to Update Manager using the aptdaemon backend for installing packages in Maverick, as opposed to the Synaptic backend that it used to use earlier. Thanks to some PolicyKit magic, aptdaemon doesn't require you to authenticate to check for updates.

It is of course a deliberate change, and is overall an improvement over the old situation for various reasons. Such behavior isn't guaranteed to be absolutely consistent over Ubuntu releases; it's usually not possible to improve things without changing them around.

 I appreciate the response. 

Unlike another poster, who FTCRTP (and I appreciate your taking the time to make the point for me); I was not sure if this just a screw up, considering the amount of source code; or, as you point out, a deliberate change. 

Now, I can go back to the people who are the `guinea pigs` in my company, and be able to explain WHY the behavior changed. Whether they like it, or accept or not; there is an answer to the question: &quot;Why did this change?&quot;  

<snip>

---

