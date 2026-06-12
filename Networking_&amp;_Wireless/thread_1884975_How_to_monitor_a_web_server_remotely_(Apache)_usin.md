---
title: "How to monitor a web server remotely (Apache) using a shell script"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by zero-n on 2011-11-22
How to monitor a web server remotely (Apache) using a shell script?

---

### Post by Lars Noodén on 2011-11-22
What do you want to monitor about it?  Do you mean wrapping curl or wget in a script to see if a page is available or not?

For full network monitoring, which might be overkill, you can use Nagios, Cacti, or Zabbix.

---

### Post by zero-n on 2011-11-22
i want to check if Apache is working or not.

Nagios, Cacti, or Zabbix is far more than what i need

i have used Nagios before

nagios have plug-in called check_http but it binary as i think

i need a shell script to check Apache remotely

---

### Post by Lars Noodén on 2011-11-22
[curl](http://manpages.ubuntu.com/manpages/precise/en/man1/curl.1.html) allows you to fetch just the headers.  The following is a little crude and inflexible but works for some [status codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html).

```

curl --silent --head http://www.example.org/  \
  | egrep "20[0-9] Found|30[0-9] Found" >/dev/null && echo OK || echo Not Found

```

---

### Post by zero-n on 2011-11-22
i've edited your code to check for [www.google.com]("http://www.google.com")
```

#!/bin/bash
curl --silent --head http://www.google.com/ | egrep "20[0-9] Found|30[0-9] Found" >/dev/null && echo OK || echo Not Found

```but the result is always [COLOR=Red]Not Found[/COLOR]

---

### Post by Lars Noodén on 2011-11-22
> **zero-n said:**
> but the result is always [COLOR=Red]Not Found[/COLOR]

For me it works for both [www.google.com](www.google.com) and for example.org.   What output do you get for just curl?

```

curl --silent --head http://www.google.com/ 

```

There is also another way to write the script:
```

if curl --silent --head http://www.google.com/  |egrep "20[0-9] Found|30[0-9] Found" >/dev/null
then
  echo Running
else
  echo Not Running
fi

```

---

### Post by San_SS! on 2011-11-22
You can make a simple python script like this:

```

import httplib
try:
    conn = httplib.HTTPConnection("www.google.com")
    conn.request("HEAD", "/")
    res = conn.getresponse()
    print "Received response"
except:
    print "Something is broken"

```

Here any exceptions are caught, name resolution problems connection problems.  If you want to be more specific you can catch particular exceptions.

---

### Post by zero-n on 2011-11-22
sorry for inconvenience script is running ok now the problem were with my proxy the http_proxy environment variable was not set to my proxy server

---

