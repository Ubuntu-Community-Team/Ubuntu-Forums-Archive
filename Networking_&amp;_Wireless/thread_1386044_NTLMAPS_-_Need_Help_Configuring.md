---
title: "NTLMAPS - Need Help Configuring"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2010-01-20
Hello,

I'm trying to get ntlmaps working against my company's new proxy.

Without ntlmaps, I'm able to surf in firefox, after authenticating via the challenge that pops up.

However, when trying non-ntlm-authenticating apps, for instance, wget, I can't download files.

Therefore, I installed and am trying to configure ntlmaps, but I'm having a hard time. I'm not going to try to interpret what the problem is, because I don't know what's going on, so I'll show you my config, my logs, and what I'm seeing with wget.

I'm including wget output, three ntlmaps logging files, and my server.cfg. Hopefully, you'll be able to spot the problem.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2010-01-20
I should show the wget output, I suppose, as this is where the rubber meets the road.

Note that I've replaced a potentially sensitive IP and hostname with dummy data.

```
jamie@mercury:~/garbage/sensitive$ wget --no-check-certificate -d http://www.cnn.com
DEBUG output created by Wget 1.11.4 on linux-gnu.

--2010-01-19 16:39:27--  http://www.cnn.com/
Resolving localhost... 127.0.0.1
Caching localhost => 127.0.0.1
Connecting to localhost|127.0.0.1|:5865... connected.
Created socket 3.
Releasing 0x089c5160 (new refcount 1).

---request begin---
GET http://www.cnn.com/ HTTP/1.0
User-Agent: Wget/1.11.4
Accept: */*
Host: www.cnn.com

---request end---
Proxy request sent, awaiting response... 
---response begin---
HTTP/1.0 307 Proxy Redirect
Mime-Version: 1.0
Date: Tue, 19 Jan 2010 15:39:27 CST
Content-Type: text/html
Cache-Control: no-cache
Location: https://zzz-proxy.zzzi.com/B0000D0000N0001/http://www.cnn.com/
Connection: close
Content-Length: 1140

---response end---
307 Proxy Redirect
Location: https://zzz-proxy.zzzi.com/B0000D0000N0001/http://www.cnn.com/ [following]
Closed fd 3
--2010-01-19 16:39:28--  https://zzz-proxy.zzzi.com/B0000D0000N0001/http://www.cnn.com/
Resolving zzz-proxy.zzzi.com... 10.19.255.255
Caching zzz-proxy.zzzi.com => 10.19.255.255
Connecting to zzz-proxy.zzzi.com|10.19.255.255|:443... connected.
Created socket 3.
Releasing 0x08a3a7c8 (new refcount 1).
Initiating SSL handshake.
Handshake successful; connected socket 3 to SSL handle 0x08a3a818
certificate:
  subject: /C=US/postalCode=22555/ST=MD/L=Baltimore/streetAddress=1000 main st./O=zzz International/OU=zzz CIT/OU=Secure Link SSL Pro/CN=zzz-proxy.zzzi.com
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
Date: Tue, 19 Jan 2010 15:39:28 CST
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

<p><br> Please refer to the zzz International Acceptable Use Policy regarding the acceptable use of public web sites.  <br> <br> <br>  If you feel that you have received this notification in error or you require access to the blocked site as part of your zzz work duties, please download and complete the <b>Website Access Request Form</b>, located <a href="https://workspace.zzzi.com/finance/cit/servicedesk/Shared%20Documents/Blank%20Forms%20-%20Public/Blocked_Web_Site_Access_Approval_Form.pdf" target="_blank">HERE</a> and email the completed form to the zzz HelpDesk at helpdesk@zzzi.com. <br> <br></p>

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

---

### Post by Jamie Jackson on 2010-02-02
I have given up on NTLMAPS. I can't get support for it, and it seems it's been obsoleted by cntlm, anyway.

Unfortunately, I'm also having trouble configuring cnltm. Please see [my other topic about cntlm]("http://ubuntuforums.org/showthread.php?t=1396749").

Thanks,
Jamie

---

