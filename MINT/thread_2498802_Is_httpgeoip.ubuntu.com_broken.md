---
title: "Is http://geoip.ubuntu.com broken?"
date: 2024-06-27
forum: MINT
---

### Post by 20c on 2024-06-27
Not sure how to get support with this.

Linux Mint user here. I recently realized I can no longer find out my location:
[LIST]
[*]in my browser
[*]when trying to find the nearest mirror for my sources
[*]or just to adjust automatically my screen temperature when the night comes.
[/LIST]

It is worth noting that my public IP also changed recently, when my ISP installed my fiber access.

Doing some searches, it seems that, at least for the mirror search, Lilnux Mint queries this URL: [http://geoip.ubuntu.com/lookup](http://geoip.ubuntu.com/lookup)

When I try it manually, I get the following error.
```

MOD_PYTHON ERROR

ProcessId:      19530
Interpreter:    'geoip.ubuntu.com'

ServerName:     'geoip.ubuntu.com'
DocumentRoot:   '/srv/geoip.ubuntu.com/www'

URI:            '/lookup'
Location:       '/lookup'
Directory:      None
Filename:       '/srv/geoip.ubuntu.com/cgi-bin/lookup.py'
PathInfo:       ''

Phase:          'PythonHandler'
Handler:        'lookup'

Traceback (most recent call last):

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/srv/geoip.ubuntu.com/cgi-bin/lookup.py", line 61, in handler
    req.write(ans)

UnicodeEncodeError: 'ascii' codec can't encode character u'\xce' in position 227: ordinal not in range(128)

MOD_PYTHON ERROR

ProcessId:      19530
Interpreter:    'geoip.ubuntu.com'

ServerName:     'geoip.ubuntu.com'
DocumentRoot:   '/srv/geoip.ubuntu.com/www'

URI:            '/lookup'
Location:       '/lookup'
Directory:      None
Filename:       '/srv/geoip.ubuntu.com/cgi-bin/lookup.py'
PathInfo:       ''

Phase:          'PythonHandler'
Handler:        'lookup'

Traceback (most recent call last):

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/srv/geoip.ubuntu.com/cgi-bin/lookup.py", line 61, in handler
    req.write(ans)

UnicodeEncodeError: 'ascii' codec can't encode character u'\xce' in position 227: ordinal not in range(128)

```

Is the website broken? Or is there something special about my IP that is not supported? Or something else?

---

### Post by currentshaft on 2024-06-27
When you try what manually?

Run this command to see if your computer can reach that URL:

curl -vvv [https://geoip.ubuntu.com/lookup](https://geoip.ubuntu.com/lookup)

---

### Post by deadflowr on 2024-06-27
*Thread moved to **MINT***

---

### Post by 20c on 2024-06-28
Here's the CURL output: [https://annuel2.framapad.org/p/curl-output-a8k8](https://annuel2.framapad.org/p/curl-output-a8k8)

(somehow pasting this text in the message body results in some permission denied error of the forum)

---

### Post by joe73 on 2024-09-24
same problem for me.
Where to report this very annoying problem?

---

### Post by thecyclops on 2024-10-03
> **20c said:**
> Not sure how to get support with this.

Linux Mint user here. I recently realized I can no longer find out my location:
[LIST]
[*]in my browser
[*]when trying to find the nearest mirror for my sources
[*]or just to adjust automatically my screen temperature when the night comes.
[/LIST]

It is worth noting that my public IP also changed recently, when my ISP installed my fiber access.

Doing some searches, it seems that, at least for the mirror search, Lilnux Mint queries this URL: [http://geoip.ubuntu.com/lookup](http://geoip.ubuntu.com/lookup)

When I try it manually, I get the following error.
```

MOD_PYTHON ERROR

ProcessId:      19530
Interpreter:    'geoip.ubuntu.com'

ServerName:     'geoip.ubuntu.com'
DocumentRoot:   '/srv/geoip.ubuntu.com/www'

URI:            '/lookup'
Location:       '/lookup'
Directory:      None
Filename:       '/srv/geoip.ubuntu.com/cgi-bin/lookup.py'
PathInfo:       ''

Phase:          'PythonHandler'
Handler:        'lookup'

Traceback (most recent call last):

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/srv/geoip.ubuntu.com/cgi-bin/lookup.py", line 61, in handler
    req.write(ans)

UnicodeEncodeError: 'ascii' codec can't encode character u'\xce' in position 227: ordinal not in range(128)

MOD_PYTHON ERROR

ProcessId:      19530
Interpreter:    'geoip.ubuntu.com'

ServerName:     'geoip.ubuntu.com'
DocumentRoot:   '/srv/geoip.ubuntu.com/www'

URI:            '/lookup'
Location:       '/lookup'
Directory:      None
Filename:       '/srv/geoip.ubuntu.com/cgi-bin/lookup.py'
PathInfo:       ''

Phase:          'PythonHandler'
Handler:        'lookup'

Traceback (most recent call last):

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.7/dist-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/srv/geoip.ubuntu.com/cgi-bin/lookup.py", line 61, in handler
    req.write(ans)

UnicodeEncodeError: 'ascii' codec can't encode character u'\xce' in position 227: ordinal not in range(128)

```

Is the website broken? Or is there something special about my IP that is not supported? Or something else?

I've been having this issue for MONTHS and finally found the solution!!!
The problem is that my city has special unicode character in it's name, and somehow this breaks python...
My solution is to use a VPN to change my location to a city without any accents, and TADA: geoip.ubunto.com/lookup works again

This is a majorly stupid but btw, and it's ridiculous that it happens considering the number of cities that have accents in them.

---

