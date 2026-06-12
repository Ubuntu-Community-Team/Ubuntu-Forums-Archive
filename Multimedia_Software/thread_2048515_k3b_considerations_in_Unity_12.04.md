---
title: "k3b considerations in Unity 12.04"
date: 2012-08-26
forum: Multimedia Software
---

### Post by parminides on 2012-08-26
For years k3b has been my choice for burning CDs. But I always felt a little uneasy that so much Kde stuff was required to install k3b (the only Kde-based program in my Gnome-based installation).

Now that I run Unity 12.04, I'm even more uneasy. The apt-get command wants to install 206MB just for k3b, including many Kde libraries!

So far I've resisted the temptation to "pollute" my Unity installation with Kde libraries. However, is there any practical reason to keep my hard drive Kde-free? Is it possible for the Kde stuff to mess something up?

When I first installed Unity, I added the LXDE environment as well. It tore up the installation. I was unable to remove it all and had to reinstall Ubuntu. (Someone said it was hard to remove because it was a metapackage.) Anyway, that experience makes me extra leery about adding k3b.

Am I worrying about nothing? Is there another CD/DVD writer that is comparable in features and reliability?

---

### Post by MG&amp;TL on 2012-08-26
> **parminides said:**
> For years k3b has been my choice for burning CDs. But I always felt a little uneasy that so much Kde stuff was required to install k3b (the only Kde-based program in my Gnome-based installation).

Now that I run Unity 12.04, I'm even more uneasy. The apt-get command wants to install 206MB just for k3b, including many Kde libraries!

So far I've resisted the temptation to "pollute" my Unity installation with Kde libraries. However, is there any practical reason to keep my hard drive Kde-free? Is it possible for the Kde stuff to mess something up?

When I first installed Unity, I added the LXDE environment as well. It tore up the installation. I was unable to remove it all and had to reinstall Ubuntu. (Someone said it was hard to remove because it was a metapackage.) Anyway, that experience makes me extra leery about adding k3b.

Am I worrying about nothing? Is there another CD/DVD writer that is comparable in features and reliability?

206 MB isn't really a massive amount. If you like k3b, go for it! It definitely shouldn't mess anything up, and it hasn't in my experience. There's several alternatives.

I find it unusual that LXDE mucked anything up. What exactly did it do? Metapackages aren't hard to remove. 

Metapackages basically don't do anything on their own, but they depend upon  other packages. So, for instance, I can install the package "ubuntu-desktop" rather than all of the packages that make up Ubuntu (some of them  metapackages themselves).

If you want to remove a metapackage *and* its dependencies,, one way to do it is to remove the metapackage and then run:

```
sudo apt-get autoremove
```which will remove all of the metapackage's dependencies, provided you haven't manually installed any of them (for instance, if you installed libreoffice before ubuntu-desktop, then removed ubuntu-desktop and autoremoved, libreoffice would remain because you'd indicated that package in particular), or needed by any other packages.

---

### Post by parminides on 2012-08-27
Thanks for the reply.

See [http://ubuntuforums.org/showthread.php?t=1967001](http://ubuntuforums.org/showthread.php?t=1967001) for details of my bad LXDE experience. In that thread no one specifically mentioned "sudo apt-get autoremove," but one person suggested a link ([http://askubuntu.com/questions/37451/find-out-what-packages-were-installed-with-a-particular-package](http://askubuntu.com/questions/37451/find-out-what-packages-were-installed-with-a-particular-package)) that said "In most cases the autoremove command of apt-get would do the trick..."

Evidently at that time I didn't figure out that "the autoremove command of apt-get" meant "sudo apt-get autoremove." You were crystal clear. It's such a simple thing that I'm surprised no one else suggested it back then. You could have saved me a lot of trouble in April!

Back to k3b, it's not the size of the dependencies that bother me. After all my problems with LXDE, I was worried about corrupting my clean Unity 12.04 with a bunch of Kde stuff. But now it looks like removal wouldn't be a problem, even if it's a metapackage.

Thanks again.

---

### Post by MG&amp;TL on 2012-08-27
> **parminides said:**
> Thanks for the reply.

See [http://ubuntuforums.org/showthread.php?t=1967001](http://ubuntuforums.org/showthread.php?t=1967001) for details of my bad LXDE experience. In that thread no one specifically mentioned "sudo apt-get autoremove," but one person suggested a link ([http://askubuntu.com/questions/37451/find-out-what-packages-were-installed-with-a-particular-package](http://askubuntu.com/questions/37451/find-out-what-packages-were-installed-with-a-particular-package)) that said "In most cases the autoremove command of apt-get would do the trick..."

Evidently at that time I didn't figure out that "the autoremove command of apt-get" meant "sudo apt-get autoremove." You were crystal clear. It's such a simple thing that I'm surprised no one else suggested it back then. You could have saved me a lot of trouble in April!

Back to k3b, it's not the size of the dependencies that bother me. After all my problems with LXDE, I was worried about corrupting my clean Unity 12.04 with a bunch of Kde stuff. But now it looks like removal wouldn't be a problem, even if it's a metapackage.

Thanks again.

Huh. Bizarre. :(

Have fun with your disc-burning activities. :)

---

