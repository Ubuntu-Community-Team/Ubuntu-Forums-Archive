---
title: "Tomboy bugs and apport-bug not working"
date: 2010-06-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2010-06-08
Just tried to report a bug via Launchpad and may have to resubmit as its not well. Tried to run Tomboy notes which doesn't open - I get the following errors when I run it via terminal:
```
$ tomboy

** (tomboy:2322): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   appindicator-sharp    (assemblyref_index=14)
     Version:    0.0.0.0
     Public Key: bcae265d1c7ab4c2
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy/).


** (tomboy:2322): WARNING **: Could not load file or assembly 'appindicator-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=bcae265d1c7ab4c2' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

```
With apport-bug (to report Tomboy) I get the following:
```
~$ apport-bug tomboy
/usr/lib/python2.6/dist-packages/apport/packaging_impl.py:93: DeprecationWarning: Attribute 'CurrentVer' of the 'apt_pkg.Package' object is deprecated, use 'current_ver' instead.
  cur_ver = self._apt_pkg(package)._pkg.CurrentVer
/usr/lib/python2.6/dist-packages/apport/packaging_impl.py:97: DeprecationWarning: Attribute 'DependsList' of the 'apt_pkg.Version' object is deprecated, use 'depends_list' instead.
  return [d[0].TargetPkg.Name for d in cur_ver.DependsList.get('Depends', []) +
/usr/lib/python2.6/dist-packages/apport/packaging_impl.py:98: DeprecationWarning: Attribute 'DependsList' of the 'apt_pkg.Version' object is deprecated, use 'depends_list' instead.
  cur_ver.DependsList.get('PreDepends', [])]
/usr/lib/python2.6/dist-packages/apport/packaging_impl.py:98: DeprecationWarning: Attribute 'TargetPkg' of the 'apt_pkg.Dependency' object is deprecated, use 'target_pkg' instead.
  cur_ver.DependsList.get('PreDepends', [])]
/usr/lib/python2.6/dist-packages/apport/packaging_impl.py:98: DeprecationWarning: Attribute 'Name' of the 'apt_pkg.Package' object is deprecated, use 'name' instead.
  cur_ver.DependsList.get('PreDepends', [])]
```

Anyone else seeing this ? I'll report back with the bug report numbers when Launchpad is better.

---

### Post by SevenMachines on 2010-06-08
yep, i get the tomboy fail and the deprecated apport things

---

### Post by SevenMachines on 2010-06-08
hmm, i now get 
$ dpkg -L libappindicator0.0-cil 
/usr/lib/cli/appindicator-sharp-0.0/appindicator-sharp.dll

instead of in appindicator-sharp-0.1, the package used to be libappindicator0.1-cli too ( the dev package is still 0.1). wonder if thats deliberate or a mistake.

thats the problem though, tomboy still looks for 0.1

---

### Post by kahumba on 2010-06-09
Tomboy could be kicked out altogether since F-Spot is being replaced by Shotwell, hence it turns out that the whole Mono stack is there just because of Tomboy and since Gnote is a good replacement it could be removed as well as the whole Mono stack and thus save a lot of space on the install CD while having new apps that start up faster and consume less memory, a win-win solution for Canonical and (pretty much) all Ubuntu users.
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-shotwell](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-shotwell)

---

### Post by davideotape on 2010-06-09
Bug for ubuntu-bug reported here: [https://bugs.edge.launchpad.net/ubuntu/+source/apport/+bug/591695](https://bugs.edge.launchpad.net/ubuntu/+source/apport/+bug/591695)

---

### Post by efmOfUb on 2010-07-04
I'm not sure this is the right place to post this bug report.

When tomboy creates an inter-tomboy link based on a new note title, it goes through and modifies the original text of all notes to create the new link. I could tolerate this behavior if it only matched exactly, but it matches loosely. And, the loose match original text is not preserved. 

So an quoted string in a note, which matches the start of the title for a different note, is silently modified to contain a hyperlink to the other note title.

I don't know what the developers intended, but this destroys data.

---

### Post by sharm on 2010-07-06
> **efmOfUb said:**
> I'm not sure this is the right place to post this bug report.

It is not. Launchpad is the place to report bugs, and your issue has nothing to do with the apport-bug error described in this thread.

> **efmOfUb said:**
> When tomboy creates an inter-tomboy link based on a new note title, it goes through and modifies the original text of all notes to create the new link. I could tolerate this behavior if it only matched exactly, but it matches loosely. And, the loose match original text is not preserved. 

So an quoted string in a note, which matches the start of the title for a different note, is silently modified to contain a hyperlink to the other note title.

I don't know what the developers intended, but this destroys data.

I'll need an example to understand what you mean about text not being preserved, and data being destroyed.  No text should be modified; it should just become linked.

---

### Post by davideotape on 2010-07-06
Yep, report a bug on Launchpad, or at least open a new post since your problem isn't the same that the OP posted!

---

### Post by dino99 on 2010-07-06
better to test the latest 1.3.1-1ubuntu1 coming into repo

---

