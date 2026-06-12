---
title: "rtmp?"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by conradin on 2012-09-15
Hi All I am trying to fetch several lectures from Cornell's rtmp server. I tried wget, amd that failed.
I tried curl that also failed. (tried installing from latest stable source too) and it still gave me the same message:
protocol rtmp not supported or disabled in libcurl. 
 
Are there any tools to help me get rtmp hosted files?
things like wget or curl?

---

### Post by conradin on 2012-09-15
Found and compiled the rtmpdump source. What i dont see is any recursive options to get all files in a directory, or all the .mp4 files.
There are persistent articles that say curl supports RTMP like this one:[http://www.thegeekstuff.com/2012/07/wget-curl/](http://www.thegeekstuff.com/2012/07/wget-curl/)

---

### Post by conradin on 2012-09-16
So to get rtmp support in curl you need librtmp. It seems odd to me but  couldn't just get that library. Oh well. 
```
sudo apt-get install build-essential gcc make subversion libssl0.9.8 libssl-dev libssl0.9.8
```
then got the rtmpdump source
```
svn co svn://svn.mplayerhq.hu/rtmpdump rtmpdump
```
then move to that directory and install
```
cd rtmpdump/trunk
```
then make an install
```
$make
$make install
```
then cd to the curl source and run ./configure where I then got the line:
```
  curl version:     7.27.0
  Host setup:       i686-pc-linux-gnu
  Install prefix:   /usr/local
  Compiler:         gcc
  SSL support:      enabled (OpenSSL)
  SSH support:      no      (--with-libssh2)
  zlib support:     enabled
  krb4 support:     no      (--with-krb4*)
  GSSAPI support:   no      (--with-gssapi)
  SPNEGO support:   no      (--with-spnego)
  TLS-SRP support:  no      (--enable-tls-srp)
  resolver:         default (--enable-ares / --enable-threaded-resolver)
  ipv6 support:     enabled
  IDN support:      no      (--with-{libidn,winidn})
  Build libcurl:    Shared=yes, Static=yes
  Built-in manual:  enabled
  --libcurl option: enabled (--disable-libcurl-option)
  Verbose errors:   enabled (--disable-verbose)
  SSPI support:     no      (--enable-sspi)
  ca cert bundle:   /etc/ssl/certs/ca-certificates.crt
  ca cert path:     no
  LDAP support:     no      (--enable-ldap / --with-ldap-lib / --with-lber-lib)
  LDAPS support:    no      (--enable-ldaps)
  RTSP support:     enabled
  RTMP support:     enabled (librtmp)
  metalink support: no      (--with-libmetalink)
  Protocols:        DICT FILE FTP FTPS GOPHER HTTP HTTPS IMAP IMAPS POP3 POP3S RTMP RTSP SMTP SMTPS TELNET TFTP
```

great, so now its going to work! ... right??
did $make and $make install in the curl directory.

the moment of truth:
```
$ curl rtmp://s12kj1swe9ii1t.cloudfront.net/cfx/st/mp4:cs145/videos/01-01-introduction.mp4 
curl: (1) Protocol rtmp not supported or disabled in libcurl

```

well now what?
config said it was enabled, and it was in the list of supported protocols... ...??

---

### Post by spjackson on 2012-09-16
> **conradin said:**
> 
```
  curl version:     7.27.0
  Host setup:       i686-pc-linux-gnu
  Install prefix:   /usr/local

```great, so now its going to work! ... right??
did $make and $make install in the curl directory.

the moment of truth:
```
$ curl rtmp://s12kj1swe9ii1t.cloudfront.net/cfx/st/mp4:cs145/videos/01-01-introduction.mp4 
curl: (1) Protocol rtmp not supported or disabled in libcurl

```well now what?
config said it was enabled, and it was in the list of supported protocols... ...??
The Install prefix means that "make install" will have installed it in /usr/local/bin. Are you sure you are running this, or are you running the old one in /usr/bin?

---

### Post by conradin on 2012-09-17
> **spjackson said:**
> The Install prefix means that "make install" will have installed it in /usr/local/bin. Are you sure you are running this, or are you running the old one in /usr/bin?

```
$ which curl
/usr/local/bin/curl

```

is that an acceptable way to tell which version Im running?

---

### Post by spjackson on 2012-09-17
In that case, I'm not sure. Perhaps you need to build libcurl3 with rtmp support and then build curl, but I don't really know.

---

### Post by SeijiSensei on 2012-09-17
At the prompt, type "echo $PATH".  You'll see the order in which directories are accessed when you run an executable program from the command prompt.  Usually /usr/local/bin is ahead of /usr/bin.

---

