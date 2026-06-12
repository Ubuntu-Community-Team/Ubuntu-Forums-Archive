---
title: "App packaging model for Ubuntu Phone/Touch: LGPL friendly?"
date: 2013-05-05
forum: Mobile Technology Discussions (CLOSED)
---

### Post by JeroMiya on 2013-05-05
I'm wondering if the packaging model for apps that will run on Ubuntu Phone or Ubuntu Touch will be compatible with LGPL licensed libraries. That is to say, can applications take dependencies on shared library packages, and can users subsequently modify the shared libraries installed by those packages, including by installing their own custom build of the LGPL library in question? There are a number of third party LGPL libraries that have been mostly unusable on mobile app platforms due to the the restrictive and bundled nature of the app packaging model, and authors of some LGPL libraries have used this fact to lock-down their LGPL library behind a pay-wall for mobile development (i.e. the author offers an alternate, more permissive license for a fee).

---

### Post by grahammechanical on 2013-05-06
What makes you think that all apps available for download on a Ubuntu Mobile device will be free to download? There are applications in the desktop Ubuntu Software Centre that are for purchase right now. Why do you think that it will be different for Ubuntu Touch? Notice this link and the heading: Choose your price.

[http://developer.ubuntu.com/publish/](http://developer.ubuntu.com/publish/)

I should think that shared libraries that are published under the GPL or LGPL can be used under the terms of those licenses. Notice the Ubuntu packaging requirements for developers wanting to get their app into the Touch app centre:

[http://developer.ubuntu.com/publish/my-apps-packages/](http://developer.ubuntu.com/publish/my-apps-packages/)

Note the point made about licencing for the Ubuntu Devleoper Preview.

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

Regards.

---

### Post by JeroMiya on 2013-05-13
Thank you for replying. However, this does not answer my question. I know that not all apps on the software center are going to be free and open source. That's fine. What I'm talking about is whether any app, open source or closed source, can comply with an LGPL license of a library it wants to use.

On the desktop, the answer is yes, because packages in the software center can 1) be shared library packages, which install dynamically linked libraries shared with multiple applications, 2) Users can write to the shared library directory themselves, overwriting any apt-get installed shared library binaries with their own, 3) Application packages in the software center can take a dependency on a shared library package in the software center, and so an application's dependencies are installed when the application is installed.

So, as an Ubuntu Linux Desktop app developer, I can be perfectly compliant with the LGPL license of a third party library when distributing my app through the software center, without releasing my own app under the LGPL (whether that means the app is closed source or some other open source license that is not LGPL compatible). 

My question, to restate, is whether this is ALSO true with applications for Ubuntu for phone and tablets. So it boils down to the following questions, to be more specific, which are left unanswered by the documentation thus far:
1) Is it possible to list shared library packages on the Ubuntu Software Center for installation on the phone and tablet version of ubuntu?
2) Can applications, though self contained in their own right, depend on shared library packages also in the store, such that any shared library package dependencies are installed, if not already, when the application is installed, just as they would be on the desktop?
3) Can end users modify the shared library directories, in order to overwrite shared libraries with, for example, their own builds? By that I mean, by any means, such as tethering the phone to a PC, or hooking it up to an external monitor+keyboard+mouse and accessing a desktop mode of some kind?

---

### Post by Nr90 on 2013-05-17
I think the aim is to have one OS running on all devices. If this is the case packaging would be the same on mobile and PC.
Currently you can install the same packages on mobile using regular apt.
Therefor I'd say shared library's should not be a problem.

One thing that might be relevant is the current development where Canonical seems to be considering a new packaging format which would provide fully self contained apps packaged with their own library's.

---

