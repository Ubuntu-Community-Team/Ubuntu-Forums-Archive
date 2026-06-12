---
title: "Ubuntu bash command equivalent to cygwin &quot;curl&quot;?"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by ffrr on 2010-05-27
Hi everybody,

I have a Cygwin script that connects to a web site with the bash command "curl". Phasing out Windows, I need to port everything to Linux. Ubuntu bash doesn't recognize "curl". There has got to be an equivalent. What would it be? Beneath the dashed line the top of the cygwin man page.

Frederic 

 And while on the topic of the bash commands available on Ubuntu, where could I find an exhaustive list?
  

---------------------------------------------------------------------------------------------------------------------

curl(1)                           Curl Manual                          curl(1) 
 
NAME 
       curl - transfer a URL 
 
SYNOPSIS 
       curl [options] [URL...] 
 
DESCRIPTION 
       curl  is  a  client  to get documents/files from or send documents to a 
       server, using any of the supported protocols (HTTP, HTTPS, FTP, GOPHER, 
       DICT,  TELNET,  LDAP  or FILE). The command is designed to work without 
       user interaction or any kind of interactivity. 
 
       curl offers a busload of useful tricks like proxy support, user authen- 
       tication,  ftp  upload,  HTTP  post, SSL (https:) connections, cookies, 
       file transfer resume and more. 
 
URL 
       The URL syntax is protocol dependent. You'll find a  detailed  descrip- 
       tion in RFC 2396. 
 
       You  can  specify  multiple  URLs or parts of URLs by writing part sets 
       within braces as in: 
 
        http://site.{one,two,three}.com 
 
       or you can get sequences of alphanumeric series by using [] as in: 
 
        ftp://ftp.numericals.com/file[1-100].txt 
        ftp://ftp.numericals.com/file[001-100].txt    (with leading zeros) 
        ftp://ftp.letters.com/file[a-z].txt 
 
       It is possible to specify up to 9 sets or series  for  a  URL,  but  no 
       nesting is supported at the moment: 
 
        http://www.any.org/archive[1996-1999]/vol- 
       ume[1-4]part{a,b,c,index}.html 
 
       You can specify any amount of URLs on the command line.  They  will  be 
       fetched in a sequential manner in the specified order. 
 
       Curl will attempt to re-use connections for multiple file transfers, so 
       that getting many files from the same server will not do multiple  con- 
       nects / handshakes. This improves speed. Of course this is only done on 
       files specified on a single command line and  cannot  be  used  between 
       separate curl invokes.

---

### Post by VastOne on 2010-05-27
> **ffrr said:**
> Hi everybody,

I have a Cygwin script that connects to a web site with the bash command "curl". Phasing out Windows, I need to port everything to Linux. Ubuntu bash doesn't recognize "curl". There has got to be an equivalent. What would it be? Beneath the dashed line the top of the cygwin man page.

Frederic 

 And while on the topic of the bash commands available on Ubuntu, where could I find an exhaustive list?
  

---------------------------------------------------------------------------------------------------------------------

curl(1)                           Curl Manual                          curl(1) 
 
NAME 
       curl - transfer a URL 
 
SYNOPSIS 
       curl [options] [URL...] 
 
DESCRIPTION 
       curl  is  a  client  to get documents/files from or send documents to a 
       server, using any of the supported protocols (HTTP, HTTPS, FTP, GOPHER, 
       DICT,  TELNET,  LDAP  or FILE). The command is designed to work without 
       user interaction or any kind of interactivity. 
 
       curl offers a busload of useful tricks like proxy support, user authen- 
       tication,  ftp  upload,  HTTP  post, SSL (https:) connections, cookies, 
       file transfer resume and more. 
 
URL 
       The URL syntax is protocol dependent. You'll find a  detailed  descrip- 
       tion in RFC 2396. 
 
       You  can  specify  multiple  URLs or parts of URLs by writing part sets 
       within braces as in: 
 
        http://site.{one,two,three}.com 
 
       or you can get sequences of alphanumeric series by using [] as in: 
 
        ftp://ftp.numericals.com/file[1-100].txt 
        ftp://ftp.numericals.com/file[001-100].txt    (with leading zeros) 
        ftp://ftp.letters.com/file[a-z].txt 
 
       It is possible to specify up to 9 sets or series  for  a  URL,  but  no 
       nesting is supported at the moment: 
 
        http://www.any.org/archive[1996-1999]/vol- 
       ume[1-4]part{a,b,c,index}.html 
 
       You can specify any amount of URLs on the command line.  They  will  be 
       fetched in a sequential manner in the specified order. 
 
       Curl will attempt to re-use connections for multiple file transfers, so 
       that getting many files from the same server will not do multiple  con- 
       nects / handshakes. This improves speed. Of course this is only done on 
       files specified on a single command line and  cannot  be  used  between 
       separate curl invokes.

Check [_[COLOR="DarkRed"]Here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=917020")

And [_[COLOR="DarkRed"]Here for Bash Command List[/COLOR]_]("http://ss64.com/bash/")

---

### Post by SquirrelOfDoom on 2010-05-27
You should be able to install the curl package, either via Synaptic, or running "sudo apt-get install curl" from the shell.

It's also worth installing bash-doc, so you can browse the documentation using "info bash", or check the man pages for bash and bash-builtins

Phil

---

### Post by ffrr on 2010-05-27
Thank you both for your quick and very helpful advice! 

Frederic

---

