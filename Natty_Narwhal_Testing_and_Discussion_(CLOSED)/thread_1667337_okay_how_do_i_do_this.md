---
title: "okay how do i do this"
date: 2011-01-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-01-14
resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver.
how to i run this been using linux for over 4 years and have never seen this command

---

### Post by cariboo on 2011-01-14
If you are trying to do updates, there are still many missing dependencies, I've got 17 packages held back when using aptitude safe-upgrade.

---

### Post by rburkartjo on 2011-01-15
car tks just never seen. still up and running on the alpha

---

### Post by Harry33 on 2011-01-15
I think at least people who have a dev version installed (this time Natty) should learn themselves to use and understand Synaptic.
Only using terminal to "using aptitude safe-upgrade" does not tell you enough, and it does not prompt you anything.

With Synaptic you are able to test every single package update one by one, and see what happens if you install.
It also shows all dependencies of the current and newest version, all dependants.
This way you are able to solve soname changes too.

Sometimes you have to uninstall old version before a new with different soname can be installed.
I know aptitude cannot always cope with this.

Of course if a package cannot be found form repos, you cannot update it.
But at least you see what package is still missing.
Then just go and see from Launchpad, the update process and state of that particular package.

---

