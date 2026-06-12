---
title: "How to get latest version of Freevo"
date: 2009-06-04
forum: Multimedia Software
---

### Post by ebike on 2009-06-04
Hi All,

I am wanting to try out the latest version of Freevo1 (I think it may be 1.9.0). Does anyone know how to get this via svn or other means. It is not very apparent from the Freevo website, the svn version they reference is only 1.7.x

The reason I want the latest (current version I have from aptitude is 1.8.1) is that to support DVBStreamer and the livepause plugin, it seems I need a later version.

Thanks,

---

### Post by keplerspeed on 2009-06-04
You can get the latest source here: [http://sourceforge.net/project/showfiles.php?group_id=46652](http://sourceforge.net/project/showfiles.php?group_id=46652) latest being version 1.9.0

And follow this guide to install: [http://doc.freevo.org/FreevoAptUbuntu](http://doc.freevo.org/FreevoAptUbuntu)

---

### Post by ebike on 2009-06-04
Wow, that was fast .. thanks.:p

---

### Post by ebike on 2009-06-05
Ok, I have run the script, all compiled ok.

However it does not run, I get the following error:
> ~/freevo/bin$ ./freevo 
Traceback (most recent call last):
  File "./freevo", line 516, in <module>
    (opts, args) = parse_options(defaults, versions)
  File "./freevo", line 401, in parse_options
    usage=help_usage % '\n  '.join(get_helpers()), version='%prog-' + versions['version'])
KeyError: 'version'


Anyone know why this error occurs?

Thanks

---

### Post by ebike on 2009-06-06
Ok, I spotted my problem to having an older version of Freevo installed by aptitude that was interfering with the newer install.

So .. I removed Freevo with "aptitude purge freevo" and got the latest 1.9.0 installed ..

However now I get a run-time error:

>   freevo
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named freevo
Traceback (most recent call last):
  File "freevo/bin/freevo", line 491, in <module>
    python, freevo_python = get_python(1)
  File "freevo/bin/freevo", line 218, in get_python
    child.fromchild.close()
AttributeError: 'Popen' object has no attribute 'fromchild'


---

### Post by ebike on 2009-06-08
Anyone?

---

### Post by mrbandersnatch on 2009-06-13
Okay I WAS getting the error "kaa.base not installed" installing the sourceforge versions. I had to run "svn co svn://svn.freevo.org/kaa/trunk/ kaa" and install from that.

Re the "AttributeError: 'Popen' object has no attribute 'fromchild' " error, is it possible you are using an older version of python? "python -V" should tell you and you *should* be running 2.6.2.

---

### Post by ebike on 2009-06-13
Hi, I have found the answer, because I was installing to a local directory (in my case ~/freevo ) I was not setting the PYTHONPATH path correctly, I had to give the following command:

> export PYTHONPATH=~/freevo/lib/python2.6/site-packages

Now it works just fine.

By the way, does anyone know why putting this command in a script file, making it executable, does not work?

I am wanting to put a number of things in a script file before I call freevo, and this was one of them ..

Thanks,

---

