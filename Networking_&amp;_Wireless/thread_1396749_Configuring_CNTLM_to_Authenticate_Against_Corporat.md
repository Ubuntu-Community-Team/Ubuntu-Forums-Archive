---
title: "Configuring CNTLM to Authenticate Against Corporate Firewall"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2010-02-02
I posted [another thread]("http://ubuntuforums.org/showthread.php?t=1386044") asking about ntlmaps, but I've given up on that, as I couldn't get it configured, and it seems that even though ntlmaps still seems more popular, it's been obsoleted by cntlm.

Anyway, my company imposed a proxy server which requires NTLM authentication, and as a result, non-NTLM clients don't work. I'm trying now to configure cntlm, but haven't figured out how to configure it for my proxy yet.

Please help me get this configured?

I [posted to the cntlm forums]("http://sourceforge.net/projects/cntlm/forums/forum/702676/topic/3531467"), but that place is a ghost town.

Juicy details:

Failing wget (no *local* proxy in use), for reference:
```

jamie@mercury:~/garbage/sensitive$ wget --no-check-certificate -d http://www.cnn.com
DEBUG output created by Wget 1.11.4 on linux-gnu.

--2010-01-26 14:57:02--  http://www.cnn.com/
Resolving www.cnn.com... 157.166.255.18, 157.166.255.19, 157.166.224.25, ...
Caching www.cnn.com => 157.166.255.18 157.166.255.19 157.166.224.25 157.166.224.26 157.166.226.25 157.166.226.26
Connecting to www.cnn.com|157.166.255.18|:80... connected.
Created socket 3.
Releasing 0x09627d08 (new refcount 1).

---request begin---
GET / HTTP/1.0
User-Agent: Wget/1.11.4
Accept: */*
Host: www.cnn.com
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 
---response begin---
HTTP/1.0 307 Proxy Redirect
Mime-Version: 1.0
Date: Tue, 26 Jan 2010 13:57:02 CST
Content-Type: text/html
Cache-Control: no-cache
Location: https://zzz-proxy.zzzi.com/B0000D0000N0001/http://www.cnn.com/
Connection: close
Content-Length: 1140

---response end---
307 Proxy Redirect
Location: https://zzz-proxy.zzzi.com/B0000D0000N0001/http://www.cnn.com/ [following]
Closed fd 3
--2010-01-26 14:57:03--  https://zzz-proxy.zzzi.com/B0000D0000N0001/http://www.cnn.com/
Resolving zzz-proxy.zzzi.com... 10.XX.XX.XX
Caching zzz-proxy.zzzi.com => 10.XX.XX.XX
Connecting to zzz-proxy.zzzi.com|10.XX.XX.XX|:443... connected.
Created socket 3.
Releasing 0x09633568 (new refcount 1).
Initiating SSL handshake.
Handshake successful; connected socket 3 to SSL handle 0x09633dd0
certificate:
  subject: /C=US/postalCode=22222/ST=OK/L=Springfield/streetAddress=123 Main St./O=zzz International/OU=zzz CIT/OU=Secure Link SSL Pro/CN=zzz-proxy.zzzi.com
  issuer:  /C=US/O=Network Solutions L.L.C./CN=Network Solutions Certificate Authority
WARNING: cannot verify zzz-proxy.zzzi.com's certificate, issued by `/C=US/O=Network Solutions L.L.C./CN=Network Solutions Certificate Authority':
  Unable to locally verify the issuer's authority.

---request begin---
GET /B0000D0000N0001/http://www.cnn.com/ HTTP/1.0
User-Agent: Wget/1.11.4
Accept: */*
Host: zzz-proxy.zzzi.com
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 
---response begin---
HTTP/1.0 401 Authorization Required
Mime-Version: 1.0
Date: Tue, 26 Jan 2010 13:57:03 CST
Content-Type: text/html
WWW-Authenticate: NTLM
WWW-Authenticate: Negotiate
Connection: keep-alive
Content-Length: 2208

---response end---
401 Authorization Required
Registered socket 3 for persistent reuse.
Skipping 2208 bytes of body: [<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Notification: WWW Authorization Required</title>
<style type="text/css">
<!--
body {
    margin-left: 2%;
    margin-right: 2%;
}
p {
    font-family: verdana, Arial, Helvetica, sans-serif;
    font-size: 12px;
    top: 0px;
    margin-top: 6px;
    margin-bottom: 6px;
}
td {
    font-family: verdana, Arial, Helvetica, sans-serif;
    font-size: 12px;
    top: 0px;
}
.code {
    font-family: courier;
    font-size: 12px;
    top: 0px;
}
h1 {
    font-family: verdana, Arial, Helvetica, sans-serif;
    font-size: 16px;
    margin-top: 24px;
    margin-bottom: 8px;
}
hr {
    margin-top: 2px;
    margin-bottom: 2px;
}
-->
</style>
</head>

<body>
<img src="http://www.zzzi.com/images/zzzi-logo.gif" border="0">
<h1>This Page Cannot Be Displayed</h1>
<hr>

<p>
Authentication is required to access the requested web site (&nbsp;zzz-proxy.zzzi.com&nbsp;).
A valid user ID and password must be entered when prompted.
</p>

<p>
If you have questions, need assistance with your login
information, or feel this is an error, please contact
zzz International HelpDesk (&nbsp;<a href="mailto:helpdesk@zzzi.com">helpdesk@zzzi.com</a>&nbsp;)
and provide the codes shown below.
</p>

<hr>
<table>
  <tr valign="top">
    <td valign="top" width="10%">Notification&nbsp;codes:&nbsp;</td>
    <td valign="top" class="code" width="90%">(1, WWW_AUTH_REQUIRED, zzz-proxy.zzzi.com)</td>
  </tr>
</table>

</body>
</html>
] done.
Authorization failed.

```
...so, that's why I'm trying to implement the local proxy to authenticate against this upstream proxy.

Here's the cntlm config:
```
Code:
Proxy		zzz-proxy.zzzi.com:443
Listen		3128
Header		User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)
Auth NTLM
```

And here's the autodetect output (option -M):
```

#note, the following fails the same way, regardless of whether i use "-u myUserId" or "-u domain\myUserID", i just tried the latter on a whim
jamie@mercury:~/garbage/sensitive$ cntlm -v -f -I -d zzz-hq -u zzz-hq\myUserId -c ~/garbage/sensitive/cntlm.conf -M http://www.cnn.com
cntlm: Proxy listening on 127.0.0.1:3128
cntlm: Resolving proxy zzz-proxy.zzzi.com...
Password: 
Config profile  1/11... Auth request ignored (HTTP code: 0)
Config profile  2/11... Auth request ignored (HTTP code: 0)
Config profile  3/11... Auth request ignored (HTTP code: 0)
Config profile  4/11... Auth request ignored (HTTP code: 0)
Config profile  5/11... Auth request ignored (HTTP code: 0)
Config profile  6/11... Auth request ignored (HTTP code: 0)
Config profile  7/11... Auth request ignored (HTTP code: 0)
Config profile  8/11... Auth request ignored (HTTP code: 0)
Config profile  9/11... Auth request ignored (HTTP code: 0)
Config profile 10/11... Auth request ignored (HTTP code: 0)
Config profile 11/11... Auth request ignored (HTTP code: 0)
You have used wrong credentials, bad URL or your proxy is quite insane,
in which case try submitting a Support Request.

```

/var/log/syslog:
```

Jan 26 14:52:55 mercury cntlm: Starting cntlm version 0.35.1 for LITTLE endian
Jan 26 14:52:55 mercury cntlm: Proxy listening on 127.0.0.1:3128
Jan 26 14:52:55 mercury cntlm: Resolving proxy zzz-proxy.zzzi.com...
Jan 26 14:52:56 mercury nss_wins[7670]: Workstation name used: mercury
Jan 26 14:53:00 mercury nss_wins[7670]: Using proxy 10.XX.XX.XX:443
Jan 26 14:53:02 mercury nss_wins[7670]: Terminating with 0 active threads
```

Thanks,
Jamie

---

### Post by Jamie Jackson on 2010-02-03
There are several mentions of Cntlm's "wiki" on the project's [home page]("http://cntlm.sourceforge.net/"), but I can't find this wiki, and its supposed links seem to go elsewhere.

I can't seem to get community help for configuring a local proxy, but maybe if somebody knows where the wiki went, I might be able to help myself. So... please let me know if you have any info about the whereabouts or contents of the wiki.

Thanks,
Jamie

From: [http://cntlm.sourceforge.net/]("http://cntlm.sourceforge.net/")

> Troubleshooting

If you have problems, you can see what's going on in the system logger (Linux: daemon.log, messages or syslog in /var/log/; on Windows using Control Panels - Administration - Logging) or run Cntlm from the command line with -v -f (debug mode). If that doesn't give you a hint, look at our [Wiki]("http://cntlm.wiki.sourceforge.net/") for troubleshooting tips and also check out the [Help Forum]("http://sourceforge.net/forum/forum.php?forum_id=702676") and the [Bug Tracker]("http://sourceforge.net/tracker/?group_id=197861&atid=963162") to see if somebody else didn't have a similar problem. When you are out of your wits and none of this helped, read the last chapter of our [Wiki]("http://cntlm.wiki.sourceforge.net/") and see how to request support.

---

### Post by Jamie Jackson on 2010-02-09
FWIW, I contacted the project's owner, asking both for support, as well as the whereabouts of the wiki.

He didn't answer my support question, but did mention that the the broken wiki links must be due to SourceForge's recent-ish restructuring. He said that he'd go looking for the wiki.

I'm still looking for an answer to my original question, so please let me know if you have any tips!

---

### Post by Jamie Jackson on 2010-02-19
Bump?

---

### Post by wolverine2k on 2010-02-26
Hey Guys,

Any answers here? I have run into the same stupid problem with my new corporate proxy/firewall. I am exactly getting the same errors as posted by James.

Any solution, anybody? It seems cntlm does not send the basic clear text password that is required by the server. I will paste in my debug output here. Please help me.

naresh@naresh-laptop:~$ wget --no-check-certificate -d [http://www.cnn.com](http://www.cnn.com)
DEBUG output created by Wget 1.11.4 on linux-gnu.

--2010-02-26 11:47:06--  [http://www.cnn.com/](http://www.cnn.com/)
Resolving localhost... 127.0.0.1, ::1
Caching localhost => 127.0.0.1 ::1
Connecting to localhost|127.0.0.1|:5065... connected.
Created socket 3.
Releasing 0x090dbd90 (new refcount 1).

---request begin---
GET [http://www.cnn.com/](http://www.cnn.com/) HTTP/1.0
User-Agent: Wget/1.11.4
Accept: */*
Host: [www.cnn.com](www.cnn.com)

---request end---
Proxy request sent, awaiting response... 
---response begin---
HTTP/1.1 407 Proxy Authentication Required
Proxy-Authenticate: BASIC realm="Corporate Internet Gateway"
Pragma: no-cache
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache, proxy-revalidate
Content-Length: 810
Connection: Keep-Alive
Set-Cookie: BCSI-CS0AD35501=2; Path=/
Date: Fri, 26 Feb 2010 09:44:18 GMT

---response end---
407 Proxy Authentication Required

Stored cookie [www.cnn.com](www.cnn.com) -1 (ANY) / <session> <insecure> [expiry none] BCSI-CS0AD35501 2
Closed fd 3
2010-02-26 11:47:06 ERROR 407: Proxy Authentication Required.


Thanks in advance people.
BR; Naresh

---

### Post by wolverine2k on 2010-03-10
Okay people. I guess not many people face similar problems as I am. I found out the reason why cntlm is not working with my company proxy. It is because my proxy requires a very basic primitive authentication mechanism listed in HTTP 1.0 specifications. It is known as HTTP Basic Authentication scheme.
 
The proxy server sends a BASIC Realm and the client has to respond with Proxy-Authorization: Basic "Base64encoded userid:password". And this has to happen for all the new GET requests even if the same connection has been authenticated previously.
 
I have modified CNTLM v0.35.1 to do exactly that without impacting the existing functionality. i.e. I have added support to BASIC HTTP Authentication and it works like a charm. There is a new parameter HTTPAUTH added in the cntlm.conf file which needs to be set to 1. The default value is 0. If the new parameter is not set to 1 then the first GET request will be authenticated but subsequent GETs using the same connection will fail and will lead to a lot of traffic between the client and the proxy.
 
So please make sure that you set the HTTPAUTH parameter to 1. This also should work even if NTLM authentication is asked for by the proxy. I haven't tested it but the code flow does not inhibit NTLM authentication in anyway. All it does is add the extra HTTP Authentication header if needed by the proxy. Proxy usually sends a 407 for requesting such an authentication.
 
I am attaching the modified CNTLM code with this post. I have tested it on Ubuntu Karmic and it works great with the browser, apt-get and all the softwares that can access via proxy. I have also asked the author of CNTLM David to inspect and review the changes and merge it into the main branch. Lets see when that happens. In the meantime, people facing problems with HTTP BASIC AUTH can use this version.
 
Basic steps are to download the file. Untar it in your location. Sudo and run ./configure and then make install. Modify the cntlm.conf file in /usr/local/etc and don't forget to set the HTTPAUTH parameter to 1. Run sudo cntlm. Please follow the configuration settings described on [http://cntlm.sourceforge.net/](http://cntlm.sourceforge.net/) and apply as defined.
 
Would be great to receive your comments/criticism. I will also provide a link on my site for downloading the attachment here.
 
BR; Naresh
visit me at [http://www.naresh.se/](http://www.naresh.se/)

---

### Post by wolverine2k on 2010-12-08
[http://www.naresh.se/2010/12/08/cntlm-0-35-1-modified-to-support-basic-http-auth-with-httpauth-parameter/](http://www.naresh.se/2010/12/08/cntlm-0-35-1-modified-to-support-basic-http-auth-with-httpauth-parameter/)
 
I got quite some questions on my modifications. As promised (though it has been almost a year now), I have a post on my site which hopefully answers all the questions that I have been getting. Enjoy.
 
BR; Naresh
 
visit me at
[http://www.naresh.se/](http://www.naresh.se/)

---

### Post by lazysail on 2011-02-10
Ubuntu 10.04 in a corporate environment: windows domain, behind a proxy and with a couple of web filters popping up.
 
The proxy info of the alternate cd are ignored and the system is installed without web update. I than configure network and proxy. Firefox (use system proxy setting) is working fine after two authorization: firstly proxy (user password) than a web-filter (domain\user password). System Update and Synaptic are not working (the proxy is again defined in Synaptic).

I tried: ntlmaps, cntlm and proxychain. Cntlm ([http://ubuntuforums.org/showthread.php?t=1396749](http://ubuntuforums.org/showthread.php?t=1396749)) works fine: thankyou Naresh. When cntlm is working, you see the dialogue with proxy and the web-filter but you can't get the Update Manager working (Got a single header line over 360 chars). It seems that it is not an ntlm auth problem but that Synaptic is unable to manage the double auth required since it does not produce popup windows as Firefox.

A Mac OS X under the same corporate environment works fine and behaves as Firefox: popup 
windows open, you put your login data and you get the updates. User name and password are 
stored in the wallet and next time you upgrade you don't even need to type them any more.

In [https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469](https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469) I read this comment: "This is a 
serious bug which massively hampers the adoption of Ubuntu as a corporate desktop in the vast 
majority of corporate environments".
Hope is not true.

---

### Post by wolverine2k on 2012-08-02
> **lazysail said:**
> 
 
I tried: ntlmaps, cntlm and proxychain. Cntlm ([http://ubuntuforums.org/showthread.php?t=1396749](http://ubuntuforums.org/showthread.php?t=1396749)) works fine: thankyou Naresh. 


Great, happy to help.

> **lazysail said:**
> 
When cntlm is working, you see the dialogue with proxy and the web-filter but you can't get the Update Manager working (Got a single header line over 360 chars). It seems that it is not an ntlm auth problem but that Synaptic is unable to manage the double auth required since it does not produce popup windows as Firefox.



The problem here is another bug 556293. Try the solutions proposed in there. There are patches provided but some don't work. I am personally using the modified apt.conf file. Also set the system wide proxy to the cntlm tag. That should solve your issue.

Cheers...

---

### Post by wolverine2k on 2012-08-03
Okay people, a lot of you guys wanted me to update the latest 0.92.3 release to support basic authentication.

I  have now done it and works extremely good. The repo sync behind https in 0.35 caused a hang which has been removed in this release. I am still asking for the developer Mavey to take in the changes but lets see what he has to say.

More information on how to use and stuff is at [http://www.naresh.se/2010/12/08/cntlm-0-35-1-modified-to-support-basic-http-auth-with-httpauth-parameter/](http://www.naresh.se/2010/12/08/cntlm-0-35-1-modified-to-support-basic-http-auth-with-httpauth-parameter/)

Attached is the 0.92.3 release with support for HTTPAUTH. ENJOY:popcorn:.

Cheers, Naresh

---

### Post by SudarshanS on 2012-08-24
Thank you so much!

I'm using this on a mac right now to make apps that do not support authenticating proxies work! I'm planning to do the same on my linux. Till today I was at my wits end trying to use squid for this since I'm behind a HTTPS proxy that uses basic auth which CNTLM does not support and facing slow speeds and irritating config issues.

PS: Can you please also upload a patch with your modifications so that even if you are unable to maintain this in the future, we can easily make this work with newer versions of CNTLM?

---

### Post by Princedhampir on 2012-08-27
Thanks work like a charm on fedora!

The only thing i dont know is how to start it automatically.

Good job! ):P

---

### Post by wolverine2k on 2012-08-30
> **SudarshanS said:**
> Thank you so much!
PS: Can you please also upload a patch with your modifications so that even if you are unable to maintain this in the future, we can easily make this work with newer versions of CNTLM?

Hi,

I had submitted a patch to the developer of CNTLM when it was 0.35. He came back saying that he didn't want such a functionality in his implementation. I will try submitting the new patch again. Lets see if it gets incorporated upstream.

Cheers, Naresh
[http://www.naresh.se/](http://www.naresh.se/)

---

### Post by wolverine2k on 2012-08-30
> **Princedhampir said:**
> Thanks work like a charm on fedora!

The only thing i dont know is how to start it automatically.

Good job! ):P

Put the command in /etc/rc.d/init.d and it will boot up automatically. Do tell me if it works in Fedora.

Cheers, Naresh
[http://www.naresh.se/](http://www.naresh.se/)

---

