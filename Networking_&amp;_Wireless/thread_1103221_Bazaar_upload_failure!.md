---
title: "Bazaar upload failure!"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by gangas on 2009-03-22
Hello all!

I just created a repostitory and tried to upload it to a temp directory, i want to make a small system which i can click and it will commit and upload the changes to my site, i am doing this with Bazaar Version Control.

I made the repository and try to upload, and get the following error:


```
thom@thom-desktop:~/dev/rpg/rpg3$ bzr upload ftp://gangasnl@ftp.gangas.nl/private/temp                                                                                                                       
FTP gangasnl@ftp.gangas.nl password: 
bzr: ERROR: bzrlib.errors.NoSuchRevision: KnitPackRepository('file:///home/thom/dev/rpg/rpg3/.bzr/repository/') has no revision ('thom@thom-desktop-20090321152445-9xye1pjxpc8xcgnn',)

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/bzrlib/commands.py", line 857, in run_bzr_catch_errors
    return run_bzr(argv)
  File "/usr/lib/python2.5/site-packages/bzrlib/commands.py", line 797, in run_bzr
    ret = run(*run_argv)
  File "/usr/lib/python2.5/site-packages/bzrlib/commands.py", line 499, in run_argv_aliases
    return self.run(**all_cmd_args)
  File "/usr/lib/python2.5/site-packages/bzrlib/plugins/upload/__init__.py", line 123, in run
    self.upload_tree()
  File "/usr/lib/python2.5/site-packages/bzrlib/plugins/upload/__init__.py", line 259, in upload_tree
    from_tree = self.branch.repository.revision_tree(rev_id)
  File "/usr/lib/python2.5/site-packages/bzrlib/decorators.py", line 138, in read_locked
    result = unbound(self, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/repository.py", line 1663, in revision_tree
    inv = self.get_revision_inventory(revision_id)
  File "/usr/lib/python2.5/site-packages/bzrlib/decorators.py", line 138, in read_locked
    result = unbound(self, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/repository.py", line 1627, in get_revision_inventory
    return self.get_inventory(revision_id)
  File "/usr/lib/python2.5/site-packages/bzrlib/decorators.py", line 138, in read_locked
    result = unbound(self, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/repository.py", line 1520, in get_inventory
    return self.iter_inventories([revision_id]).next()
  File "/usr/lib/python2.5/site-packages/bzrlib/repository.py", line 1538, in _iter_inventories
    for text, revision_id in self._iter_inventory_xmls(revision_ids):
  File "/usr/lib/python2.5/site-packages/bzrlib/repository.py", line 1549, in _iter_inventory_xmls
    raise errors.NoSuchRevision(self, record.key)
NoSuchRevision: KnitPackRepository('file:///home/thom/dev/rpg/rpg3/.bzr/repository/') has no revision ('thom@thom-desktop-20090321152445-9xye1pjxpc8xcgnn',)

bzr 1.6.1 on python 2.5.2 (linux2)
arguments: ['/usr/bin/bzr', 'upload', 'ftp://gangasnl@ftp.gangas.nl/private/temp']
encoding: 'UTF-8', fsenc: 'UTF-8', lang: 'nl_NL.UTF-8'
plugins:
  avahi                /usr/lib/python2.5/site-packages/bzrlib/plugins/avahi [0.3.0dev0]
  bzrtools             /usr/lib/python2.5/site-packages/bzrlib/plugins/bzrtools [1.6.0]
  dbus                 /usr/lib/python2.5/site-packages/bzrlib/plugins/dbus [unknown]
  email                /usr/lib/python2.5/site-packages/bzrlib/plugins/email [unknown]
  gtk                  /usr/lib/python2.5/site-packages/bzrlib/plugins/gtk [0.95.0]
  launchpad            /usr/lib/python2.5/site-packages/bzrlib/plugins/launchpad [unknown]
  pqm                  /usr/lib/python2.5/site-packages/bzrlib/plugins/pqm [1.0.0dev0]
  rebase               /usr/lib/python2.5/site-packages/bzrlib/plugins/rebase [0.3.0]
  svn                  /usr/lib/python2.5/site-packages/bzrlib/plugins/svn [0.4.13]
  upload               /usr/lib/python2.5/site-packages/bzrlib/plugins/upload [0.1.0]
*** Bazaar has encountered an internal error.
    Please report a bug at https://bugs.launchpad.net/bzr/+filebug
    including this traceback, and a description of what you
    were doing when the error occurred.

``` 
I have made a bug report.



I also tried it on an other repository i created... All the same!

I hope someone could help me...

Thom

---

