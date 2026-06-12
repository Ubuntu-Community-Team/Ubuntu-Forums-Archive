---
title: "compiz held back"
date: 2011-01-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ikt on 2011-01-27
Does anyone else have this issue?

No matter what I do: apt-get upgrade, apt-get dist-upgrade, update-manager -d, etc compiz will not install

[http://ikt.id.au/wp-content/uploads/2011/01/upgrade.png](http://ikt.id.au/wp-content/uploads/2011/01/upgrade.png)

---

### Post by sgage on 2011-01-27
I had it held back earlier while a bunch of packages related to compiz (including Unity) were being loaded up. Then I got a load of about 13 packages including compiz and unity in one big slug. Now they're already loading up a new compiz, it seems. Just wait until all the bits and bobs are uploaded, and it will be good. I think. I hope :-)

---

### Post by ikt on 2011-01-27
> **sgage said:**
> I had it held back earlier while a bunch of packages related to compiz (including Unity) were being loaded up. Then I got a load of about 13 packages including compiz and unity in one big slug. Now they're already loading up a new compiz, it seems. Just wait until all the bits and bobs are uploaded, and it will be good. I think. I hope :-)

yeah the problem was the aussie mirror wasn't updated, cheers :)

---

### Post by mc4man on 2011-01-27
> Now they're already loading up a new compiz, it seems.
The 2nd compiz update (to ...0ubuntu5) is removing a patch w/ a bit of history (000_workaround_gconfbackend_init_hang.patch

So if after the update, if when logging in to unity it hangs (usually a spinning cursor) then you may want to report that
(all is well here in that regard

---

### Post by ikt on 2011-01-27
> **mc4man said:**
> The 2nd compiz update (to ...0ubuntu5) is removing a patch w/ a bit of history (000_workaround_gconfbackend_init_hang.patch

So if after the update, if when logging in to unity it hangs (usually a spinning cursor) then you may want to report that
(all is well here in that regard

Would like to but now I'm getting this error!

Poor daemon :( RIP

---

### Post by mc4man on 2011-01-27
> Would like to but now I'm getting this error!
Close update manager and try again or synaptic will work.
(I've had the UM do that occasionally, usually a 2nd attempt is ok, or my typical action if unity/compiz goes a bit south is a quick logout/in

---

### Post by Harry33 on 2011-01-28
> **mc4man said:**
> Close update manager and try again or synaptic will work.
(I've had the UM do that occasionally, usually a 2nd attempt is ok, or my typical action if unity/compiz goes a bit south is a quick logout/in

People using dev cycles really ought to learn to use Synaptic with all info it shows.

---

### Post by mc4man on 2011-01-28
> People using dev cycles really ought to learn to use Synaptic with all info it shows.
Undoubtedly - nothing quite like it

the one reason I tend to use update manager first is it lists all upgrades and many times has active links to bugs fixed, (or hopefully fixed), in the 'changes', and I also  find the changes informative to glance thru. (a bit quicker than dl in synaptic

---

### Post by Harry33 on 2011-01-28
> **mc4man said:**
> Undoubtedly - nothing quite like it

the one reason I tend to use update manager first is it lists all upgrades and many times has active links to bugs fixed, (or hopefully fixed), in the 'changes', and I also  find the changes informative to glance thru. (a bit quicker than dl in synaptic

Right,

I look all the changes and the state of coming builds too from Ubuntu Lists:
[https://lists.ubuntu.com/archives/natty-changes/2011-January/date.html#start](https://lists.ubuntu.com/archives/natty-changes/2011-January/date.html#start)

---

### Post by ronacc on 2011-01-28
I prefer synaptic for several reasons , 2 of them being update-manager misses available updates and it also refuses to install anything if there is an update from an "untrusted source" , even the "trusted" updates so even if I attempt to use update-manager I end up using synaptic anyway .

---

### Post by ikt on 2011-01-28
> **Harry33 said:**
> People using dev cycles really ought to learn to use Synaptic with all info it shows.

Yeah and I wasn't even aware of it! gg

---

### Post by mc4man on 2011-01-28
speaking of synaptic - at least here can see all sorts of interesting behavior if synaptic is opened > maximized and either closed or restored and closed.
(particularly if update manager is then clicked on ...

---

### Post by Harry33 on 2011-01-29
> **mc4man said:**
> speaking of synaptic - at least here can see all sorts of interesting behavior if synaptic is opened > maximized and either closed or restored and closed.
(particularly if update manager is then clicked on ...

Update-Manager and Synaptic cannot be used at the same time.
You have to kill one or the other application.

---

### Post by mc4man on 2011-01-29
> Update-Manager and Synaptic cannot be used at the same time.
You have to kill one or the other application.
Didn't say anything about using at the same time

---

### Post by Harry33 on 2011-01-29
> **mc4man said:**
> Didn't say anything about using at the same time

Ah yes I see, you meant you clicked on update-manager package in synaptic, right.

Anyway, I do not see any such problem in my setup.
I am using Gnome-Classic without Compiz, are using Unity+Compiz?

---

### Post by mc4man on 2011-01-29
> Anyway, I do not see any such problem in my setup.
I think this would only happen in Desktop >  unity
> you clicked on update-manager package in synaptic, right.
No, separately.

What I was mentioning is related to this - 
Occasionally a utility window like update manager will open in the top left corner with the top buried under the unity bar. If it does then an Alt+click can pull it down.

When seems to happen here (2 different machines), is then, after closing the pulled down window, a new 'invisible' window is created in the general area of that closed window, though this time only on the workspace this occurred on.

One way I've found to increase the likelihood of getting a window buried at the top is to open synaptic > maximize it, then either close or restore and close.
After that, when  opening update manager, it's more likely it will get buried. (there are some other windows this could happen to like the logout window, but update manager is the one most likely to get 'buried', sometimes it takes a second opening to happen..

Other odd things can also  happen when maximizing certain windows.

---

### Post by Harry33 on 2011-01-29
> **mc4man said:**
> I think this would only happen in Desktop >  unity

No, separately.

What I was mentioning is related to this - 
Occasionally a utility window like update manager will open in the top left corner with the top buried under the unity bar. If it does then an Alt+click can pull it down.

When seems to happen here (2 different machines), is then, after closing the pulled down window, a new 'invisible' window is created in the general area of that closed window, though this time only on the workspace this occurred on.

One way I've found to increase the likelihood of getting a window buried at the top is to open synaptic > maximize it, then either close or restore and close.
After that, when  opening update manager, it's more likely it will get buried. (there are some other windows this could happen to like the logout window, but update manager is the one most likely to get 'buried', sometimes it takes a second opening to happen..

Other odd things can also  happen when maximizing certain windows.

That looks as it were a Window Manager issue (Compiz).

---

