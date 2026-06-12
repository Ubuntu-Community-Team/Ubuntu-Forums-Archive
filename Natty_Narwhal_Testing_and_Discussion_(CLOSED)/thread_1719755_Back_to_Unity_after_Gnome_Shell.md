---
title: "Back to Unity after Gnome Shell"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by snlzkn on 2011-04-02
My unity was crashing all the time with Natty Beta1 I decided to try gnome-shell from gnome3 and gnome-shell ppas. It is working but for some reason mutter is not running. Using metacity makes my windows extremely ugly. I could not find a solution to that and I really love the shortcuts in unity Super + a,f,s 1,2,3 ... and I want to install unity again.

I uninstalled ubuntu-desktop and compiz* and unity* and installed xubuntu-desktop, then I installed gnome-shell. After that I installed ubuntu-desktop to be able to use unity. Now when I select Ubuntu from the Login screen it says failed to load ubuntu.

When I write unity --replace the screen goes away and goes back to login screen saying something went wrong. 

I am fine with purging all the related libraries and reinstalling them to get unity running again and I don't mind if it breaks up gnomeshell or xubuntu. How can I achieve this?

Edit: I purged everything related to xubuntu, unity and compiz even gdm and reinstalled ubuntu-desktop and gdm back. Nothing changed. gnome shell runs without windows manager and Ubuntu or Ubuntu classical does not login. I just cannot understand how this can happen. I will try with disabling the gnome3 repo but then I will not have any working desktop managers left and I don't want that.

---

### Post by cariboo on 2011-04-02
If you got gnome-shell from a ppa, you can use ppa purge to remove it.

---

### Post by kansasnoob on 2011-04-02
I'd be surprised if you don't need to reinstall. I have one install that I've played with heavily and that's what I've decided to do with it, comparing it to other fresh installs I performed during iso-testing.

---

### Post by snlzkn on 2011-04-02
While removing some stuff I removed some important things as well I guess since I cannot login now. When I write my user name it says /home/userName cannot be accessed. But when I login as root I can see it and its owner is also userName :S I managed to login to gnome-shell as root but my wireless did not work. I am downloading 11.04 and will reinstall after 2 years :S This time I will make home a different partition!

I like the notifications of Gnome-shell but other than that it costed me a lot ;(

---

### Post by ojdon on 2011-04-02
While we're on the subject of Gnome-shell is the ppa version stable? Like last week it got rid off all the icons, themes and background to every single session as well as Gnome-shell itself. I never had any luck compiling it from git, either.

---

### Post by snlzkn on 2011-04-02
For me it was stable but for some reason no window decorator :S I  mean I had the window borders but they were extremely ugly. When I check processes with htop no mutter or metacity. When I write mutter --replace I got some errors. I did not have any troubles with icons though. Well I will install 32bit beta1 now hopefully it will be a little stable...

---

