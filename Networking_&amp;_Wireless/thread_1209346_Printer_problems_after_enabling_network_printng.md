---
title: "Printer problems after enabling network printng"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by Jamesss on 2009-07-10
I tried to set up my HP Laserjet 1100 for network printing in system-printer-config (under System/Admin/Printing) and now my printer has disappeared and I can't run system-printer-config (it crashes). Running it from the terminal produces this output - can anyone help?

```
james@james-desktop:~$ system-config-printer
/home/james/.printer-groups.xml:1: parser error : Document is empty

^
/home/james/.printer-groups.xml:1: parser error : Start tag expected, '<' not found

^
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/XmlHelper.py", line 37, in __init__
    self.xml_doc = libxml2.parseFile (self.group_file_name)
File "/var/lib/python-support/python2.6/libxml2.py", line 1279, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
parserError: xmlParseFile() failed
Continuing anyway..
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 6757, in <module>
    focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 6705, in main
    print_test_page, focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 565, in __init__
    self.groups_pane = GroupsPane ()
  File "/usr/share/system-config-printer/GroupsPane.py", line 144, in __init__
    for group_name, group_node in xml_helper.get_static_groups ():
  File "/usr/share/system-config-printer/XmlHelper.py", line 68, in get_static_groups
    return self.__parse_groups ("static-group")
  File "/usr/share/system-config-printer/XmlHelper.py", line 54, in __parse_groups
    current = self.xml_doc.getRootElement ().children
AttributeError: 'NoneType' object has no attribute 'getRootElement'

```

---

### Post by superprash2003 on 2009-07-10
printer has disappeared in the host machine?? you could remove all instances of it from sys->admin->printing and then restart the printer and click on add a new printer and search for it

---

### Post by Jamesss on 2009-07-10
Yes the printer has disappeared from the host computer. The problem is that I cannot run sys->admin->printing because although the window pops up for split second, it immediately crashes and exits. Any other ideas?

---

### Post by Jamesss on 2009-07-10
So I tried removing all programs relating to system-config-printer and reinstalling them and still it keeps crashing. How can I undo the network printer changes so I can just print normally from the host computer?
These are the programs I reinstalled:

cupsys-driver-gutenprint
cups-driver-gutenprint
ijsgutenprint
foomatic-db-gutenprint
python-foomatic
foomatic-db-hpijs
bluez-cups
cupsys
hal-cup-utils
hpijs
hplip
splix
ubuntu-desktop
cups
printconf
python-ipy
avahi-utils
cupsddk
cupsddk-drivers
libijs-0.35
libsnmp15
python-usb
sane-utils
python-smbc
system-config-printer-common
python-cupshelpers
system-config-printer-gnome

---

### Post by Jamesss on 2009-07-10
Finally! It seems I just had to delete /home/james/.printer-groups.xml

---

### Post by studiogrynn on 2009-09-17
Having the same issue, I thought that deleting the xml might be the ticket. Thanks for confirming that!

---

### Post by dustingold09 on 2009-09-18
Hi,


I think your printer ha disabled from your machine. 
You should check this link,it might be useful for you.



[Label Printer]("http://www.brother.ca")

---

