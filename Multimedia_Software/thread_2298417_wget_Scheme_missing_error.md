---
title: "wget: Scheme missing error"
date: 2015-10-10
forum: Multimedia Software
---

### Post by mamboknave on 2015-10-10
Please, follow me. I could not find solutions on the web.

$ cat wgetproblem.bsh

#! /bin/bash
page="http://site_with_no_html_estension/"
agent=" 'Windows-RSS-Platform/2.0' "
wget -S -U "$agent"  "$page"  -O /tmp/page.html
exit

Launching wgetproblem.bsh gives **"Scheme missing"** error:

$ ./wgetproblem.bsh
"http://site_with_no_html_estension/": Scheme missing.

Instead, if I launch that wget directly as command line on terminal, **it works perfectly**:

$ wget -S -U 'Windows-RSS-Platform/2.0'   "http://site_with_no_html_estension/"   -O /tmp/page.html

What am I doing wrong??

Thanks a bunch!

---

### Post by blm-ubunet on 2015-10-10
Does this work any better in your script ?
```
wget -S -U "${agent}" "${page}" -O /tmp/page.html
```

---

