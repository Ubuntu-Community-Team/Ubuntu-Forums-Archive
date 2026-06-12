---
title: "failing  to connect to x11vnc"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2009-07-29
I'm  trying  to set up VNC /apache /ssl as per 
[http://www.karlrunge.com/x11vnc/ssl-portal.html](http://www.karlrunge.com/x11vnc/ssl-portal.html)

(SSH/openVPN etc isn't an option and there is an ISA proxy in the way of port 80 connections)

and am failing to connect 

So im trying to trouble shoot it : 

I can start x11vnc 
 x11vnc  -http -display :0  -forever -rfbauth  /home/paul/.vnc/passwd    -rfbport 5915

i can access it with  a vnc viewer from my LAN 
is vncviewer zilly::5915 prompts for the pw and then gives me access

but when I try from the browser 
[https://blah/vnc/zilly](https://blah/vnc/zilly) 
it says "you dont have permission to access /vnc/zilly on this server "

ive chowned everything in /var/www/vnc to www-data  ( ive been having a try with the java viewer as well) 

[email]paul@zilly:~/.vnc[/email]$ ls -la /var/www/vnc
total 488
drwxr-xr-x 3 www-data www-data  4096 2009-07-25 08:29 .
drwxr-xr-x 3 www-data www-data  4096 2009-07-25 08:29 ..
-rwxr-xr-x 1 www-data www-data  2415 2009-07-25 08:29 AuthPanel.class
-rwxr-xr-x 1 www-data www-data  2982 2009-07-25 08:29 ButtonPanel.class
-rwxr-xr-x 1 www-data www-data  1176 2009-07-25 08:29 CapabilityInfo.class
-rwxr-xr-x 1 www-data www-data  1888 2009-07-25 08:29 CapsContainer.class
-rwxr-xr-x 1 www-data www-data 74216 2009-07-25 08:29 ChangeLog
drwxrwxrwx 2 www-data www-data  4096 2009-07-25 08:29 classes
-rwxr-xr-x 1 www-data www-data  2591 2009-07-25 08:29 ClipboardFrame.class
-rw-r--r-- 1 www-data www-data  1080 2009-07-25 08:29 compstore
-rwxr-xr-x 1 www-data www-data  7822 2009-07-25 08:29 DesCipher.class
-rw-r--r-- 1 www-data www-data   127 2009-07-25 08:29 .htaccess
-rwxr-xr-x 1 www-data www-data  1246 2009-07-25 08:29 HTTPConnectSocket.class
-rwxr-xr-x 1 www-data www-data  1885 2009-07-25 08:29 HTTPConnectSocketFactory.class
-rwxr-xr-x 1 www-data www-data  1085 2009-07-27 12:17 index.html
-rwxrwxrwx 1 www-data www-data   846 2009-07-25 08:29 index.vnc
-rwxr-xr-x 1 www-data www-data  2776 2009-07-25 08:29 InStream.class
-rwxr-xr-x 1 www-data www-data 18000 2009-07-25 08:29 LICENCE.TXT
-rwxr-xr-x 1 www-data www-data   529 2009-07-25 08:29 MemInStream.class
-rwxr-xr-x 1 www-data www-data  7066 2009-07-25 08:29 OptionsFrame.class
-rwxr-xr-x 1 www-data www-data 23030 2009-07-25 08:29 README
-rwxr-xr-x 1 www-data www-data  6011 2009-07-25 08:29 RecordingFrame.class
-rwxr-xr-x 1 www-data www-data  1405 2009-07-25 08:29 ReloginPanel.class
-rwxr-xr-x 1 www-data www-data 20536 2009-07-25 08:29 RfbProto.class
-rwxr-xr-x 1 www-data www-data  2646 2009-07-25 08:29 SessionRecorder.class
-rw-r--r-- 1 www-data www-data 64083 2009-07-25 08:29 signedVncViewer.jar
-rwxr-xr-x 1 www-data www-data   317 2009-07-25 08:29 SocketFactory.class
-rwxr-xr-x 1 www-data www-data  1584 2009-07-25 08:29 VncCanvas2.class
-rwxr-xr-x 1 www-data www-data 26719 2009-07-25 08:29 VncCanvas.class
-rw-r--r-- 1 www-data www-data   609 2009-07-25 08:29 vncCer.cer
-rwxr-xr-x 1 www-data www-data 17895 2009-07-25 08:29 VncViewer.class
-rwxr-xr-x 1 www-data www-data 61668 2009-07-25 08:29 VncViewer.jar
-rwxr-xr-x 1 www-data www-data 42603 2009-07-25 08:29 WhatsNew
-rwxr-xr-x 1 www-data www-data  1996 2009-07-25 08:29 ZlibInStream.class

xhost+ before starting x11vnc doesnt help 

 how do I troubleshoot this further ?

---

### Post by krunge on 2009-07-29
> **pdc124 said:**
> I'm  trying  to set up VNC /apache /ssl as per 
[http://www.karlrunge.com/x11vnc/ssl-portal.html](http://www.karlrunge.com/x11vnc/ssl-portal.html)

I use this ssl-portal 2-3 times a week, but I know it can be rather complicated to set up. Do you really need the full portal?  Are you redirecting to more than one internal machine running x11vnc? There are simpler solutions if there is just one internal machine to be accessed.  
> 
I can start x11vnc 
 x11vnc  -http -display :0  -forever -rfbauth  /home/paul/.vnc/passwd    -rfbport 5915

I don't think this is your immediate problem, but why aren't you supplying '-ssl SAVE' like the instructions at the ssl-portal link indicate?
> 
but when I try from the browser 
[https://blah/vnc/zilly](https://blah/vnc/zilly) 
it says "you dont have permission to access /vnc/zilly on this server "

You did this from an external machine or an internal one?

What do your apache logs say about this error?  It should have nothing to do with file permissions, but rather the apache url-rewrite rules you put in httpd.conf.

Also, are you using port 563 as the instructions suggest?  Or doing something else?  Attach all of your apache conf files (and related messages in the apache logs) to this thread and I'll have a look.

---

### Post by pdc124 on 2009-07-30
port 563 isnt open on the ISA proxy that I am behind.  Ive removed passwords etc from x11vnc to try and sort out the connection problem, then I'll add them back. 

[email]paul@zilly:~/.vnc[/email]$ x11vnc -ssl SAVE -http -display :0  -forever -rfbauth ~unixpw  -rfbport 5915

gives me 
> bQ0RkFUpfW0a28EDXDR35XDiKPlOwRt4tvU/UyOa2y+UB5x9VgORBOBFAkbymvtz
Ad6U6CMmLCO9ft5wcdUYjKaZ8k7mhPc7kcU=
-----END CERTIFICATE-----

30/07/2009 06:21:37 using PEM /home/paul/.vnc/certs/server.pem  0.017s
30/07/2009 06:21:37
30/07/2009 06:21:37
30/07/2009 06:21:37 X display :0.0 is 16bpp depth=16 true color
30/07/2009 06:21:37
30/07/2009 06:21:37 Listening for VNC connections on TCP port 5915
30/07/2009 06:21:37 openssl_port: listen on port/sock 5915/9

The SSL VNC desktop is:  zilly:15
30/07/2009 06:21:37 check_httpdir: trying to guess httpdir... x11vnc
30/07/2009 06:21:37 check_httpdir: bad guess:
30/07/2009 06:21:37    /usr/bin/../classes/ssl
30/07/2009 06:21:37
30/07/2009 06:21:37 Xinerama is present and active (e.g. multi-head).
30/07/2009 06:21:37 Xinerama: enabling -xwarppointer mode to try to correct
30/07/2009 06:21:37 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
30/07/2009 06:21:37 Xinerama: Use -noxwarppointer to force XTEST.
30/07/2009 06:21:38 fb read rate: 5 MB/sec
30/07/2009 06:21:38 screen setup finished.
30/07/2009 06:21:38

The SSL VNC desktop is:  zilly:15
PORT=5915
SSLPORT=5915


if i try to connect from the same machine 

[email]paul@zilly:~/.vnc[/email]$ telnet localhost 5915
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.


this appears in the x11vnc screen 
SSLPORT=5915
30/07/2009 06:23:28 SSL: accept_openssl(OPENSSL_VNC)
30/07/2009 06:23:28 SSL: spawning helper process to handle: 127.0.0.1:35119
30/07/2009 06:23:48 sig: 14, ssl_init timed out.
30/07/2009 06:23:48 SSL: accept_openssl: cookie from ssl_helper FAILED. 0

same thing when i try from vncviwer and a machine on my LAN and the connection fails. 

when I remove the ssl option i can at least get a vncviewer connection from the LAN.

adding xhost+ before starting x11vnc doesnt fix it (but i admit  that I dont really understand the X server/hosts/cookies/Xauth stuff)

> paul@zilly:/etc/apache2/sites-enabled$ grep ^[A-Za-z\ ] /etc/apache2/sites-enabled/ssl | grep -v '#'
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
 RewriteEngine On
   RewriteRule /vnc/([^/]+)$                        /vnc/$1/index.vnc?CONNECT=$1+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vnc_2F_$1 [R,NE,L]
   RewriteRule /vnc/proxy/([^/]+)$                  /vnc/$1/proxy.vnc?CONNECT=$1+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vnc_2F_$1&forceProxy=yes [R,NE,L]
   RewriteRule /vncs/([^/]+)$                      /vncs/$1/index.vnc?CONNECT=$1+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1 [R,NE,L]
   RewriteRule /vncs/proxy/([^/]+)$                /vncs/$1/proxy.vnc?CONNECT=$1+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&forceProxy=yes [R,NE,l]
   RewriteRule /vncs/trust/([^/]+)$                /vncs/$1/index.vnc?CONNECT=$1+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&trustAllVncCerts=yes [R,NE,L]
   RewriteRule /vncs/trust/proxy/([^/]+)$          /vncs/$1/proxy.vnc?CONNECT=$1+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&forceProxy=yes&trustAllVncCerts=yes [R,NE,L]
   RewriteRule /vnc443/([^/]+)$                    /vncs/$1/index.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1 [R,NE,L]
   RewriteRule /vnc443/proxy/([^/]+)$              /vncs/$1/proxy.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&forceProxy=yes [R,NE,L]
   RewriteRule /vnc443/trust/([^/]+)$              /vncs/$1/index.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&trustAllVncCerts=yes [R,NE,L]
   RewriteRule /vnc443/trust/proxy/([^/]+)$        /vncs/$1/proxy.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&forceProxy=yes&trustAllVncCerts=yes [R,NE,L]
   RewriteMap vnchosts txt:/etc/apache2/conf/vnc.hosts
   RewriteRule ^/vnc0.*            /VNCFAIL [F,L]
   RewriteRule ^/vnc/([^/]+)/(.*)  /vnc0/$1:http:58${vnchosts:$1|NOTFOUND}/$2  [NE]
   RewriteRule ^/vncs/([^/]+)/(.*) /vnc0/$1:https:59${vnchosts:$1|NOTFOUND}/$2 [NE]
   RewriteRule ^/vnc0.*NOTFOUND.*  /VNCFAIL [F,L]
   RewriteRule ^/vnc0/([^/]+):([^/]+):([^/]+)/(.*) $2://$1:$3/$4 [P,NE,L]
paul@zilly:/etc/apache2/sites-enabled$


from outside my LAN 
the URL 

[https://.../vnc/zilly](https://.../vnc/zilly) is rewritten to 

[https://.](https://.)... /vnc/zilly/index.vnc?CONNECT=zilly+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vnc_2F_zilly

the browser says 
Forbidden
You don't have permission to access /vnc/zilly/index.vnc on this server.
________________________________________
Apache/2.2.11 (Ubuntu) mod_ssl/2.2.11 OpenSSL/0.9.8g Server  xxxxx   Port 443


Apache acces log 
194.176.105.6 - - [30/Jul/2009:09:17:51 +0100] "GET / HTTP/1.1" 200 66 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; InfoPath.1; .NET CLR 1.1.4322)"
194.176.105.6 - - [30/Jul/2009:09:20:20 +0100] "GET /vnc/zilly HTTP/1.1" 302 331 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; InfoPath.1; .NET CLR 1.1.4322)"
195.277.105.6 - - [30/Jul/2009:09:20:20 +0100] "GET /vnc/zilly/index.vnc?CONNECT=zilly+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vnc_2F_zilly HTTP/1.1" 403 271 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; InfoPath.1; .NET CLR 1.1.4322)"
195.277.105.6 - - [30/Jul/2009:09:24:20 +0100] "GET /vnc/zilly HTTP/1.1" 302 331 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; InfoPath.1; .NET CLR 1.1.4322)"
195.277.105.6 - - [30/Jul/2009:09:31:36 +0100] "GET /vnc/zilly/index.vnc?CONNECT=zilly+5915&PORT=563&httpsPort=443&GET=1&urlPrefix=_2F_vnc_2F_zilly HTTP/1.1" 403 271 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; InfoPath.1; .NET CLR 1.1.4322)"

---

### Post by krunge on 2009-07-30
You don't seem to understand there must be a **NON-SSL** port that apache manages and has the AllowCONNECT 5915 to redirect to internal machines like zilly. The example at [http://www.karlrunge.com/x11vnc/ssl-portal.html](http://www.karlrunge.com/x11vnc/ssl-portal.html) uses 563 (but you could choose any other port, even 443, but with 443 it is still NON-SSL.)

I don't even see an AllowCONNECT in your apache config.

What happens when you follow the instructions at [http://www.karlrunge.com/x11vnc/ssl-portal.html](http://www.karlrunge.com/x11vnc/ssl-portal.html) to the letter?

If there is only one machine, i.e. zilly, you don't need to use apache at all, just do a port redir on your router: (e.g. router:443 -> zilly:5915).  

Even with more than one internal vnc host the 'connect_switch' script mentioned as an alternative at the above link can work well, and by-pass apache for the vnc as well.

---

### Post by pdc124 on 2009-08-17
sorry for the delay. its clear that my https setup wasn't correct either, and I wanted to check it from outside my LAN. That is now 
sorted. my router is forwarding 80 and 443 to  my server ( 192.168.0.100 on the LAN) and i get the expected http:// and https:// pages.  
i cant forward 443 to 5900 
I cant go toas the proxy seems to stop it  [http://blah:443](http://blah:443) 

so im using connect_switch 

root@server:# nano  /usr/local/bin/connect_switch
  GNU nano 2.0.7                          File: /usr/local/bin/connect_switch

my $listen_host = $hostname;
my $listen_port = 443;

my $httpd_host = 'localhost';
my $httpd_port = 443;

############################################################################
# You can/should override the host/port settings here:
#
$listen_host = '192.168.0.100';         # set to your interface IP number.
#$listen_port = 555;                    # and/or nonstandard port.
#$httpd_host  = 'somehost';             # maybe you redir https to another machine.
#$httpd_port  = 666;                    # and/or nonstandard port.

# You must set the allowed host:port CONNECT redirection list.
# Only these host:port pairs will be redirected to.
#
my @allowed = qw(
        machine1:5915
       localhost:5900
);




apache config 

:

    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
AccessFileName .htaccess
    Order allow,deny
    Deny from all
   RewriteEngine On
   RewriteRule /vnc443/([^/]+)$                    /vncs/$1/index.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1 [R,NE,L]
   RewriteRule /vnc443/proxy/([^/]+)$              /vncs/$1/proxy.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&forceProxy=yes [R,NE,L]
   RewriteRule /vnc443/trust/([^/]+)$              /vncs/$1/index.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&trustAllVncCerts=yes [R,NE,L]
   RewriteRule /vnc443/trust/proxy/([^/]+)$        /vncs/$1/proxy.vnc?CONNECT=$1+5915&PORT=443&httpsPort=443&GET=1&urlPrefix=_2F_vncs_2F_$1&forceProxy=yes&trustAllVncCerts=yes [R,NE,L]
root@server:/var/www/localhost/vnc#

and the apache error log file 


[Mon Aug 17 10:45:58 2009] [error] [client 127.0.0.1] File does not exist: /var/www/localhost/vnc/VncViewer.class
[Mon Aug 17 10:45:58 2009] [error] [client 127.0.0.1] File does not exist: /var/www/localhost/vnc/VncViewer
[Mon Aug 17 10:47:34 2009] [error] [client 127.0.0.1] File does not exist: /var/www/localhost/vnc/VncViewer.class
[Mon Aug 17 10:47:34 2009] [error] [client 127.0.0.1] File does not exist: /var/www/localhost/vnc/VncViewer
 ( but the files fo exist! )


and the command line after starting x11vnc
17/08/2009 11:04:55 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
17/08/2009 11:04:55
17/08/2009 11:04:55 Autoprobing TCP port
17/08/2009 11:04:55 Autoprobing selected port 5900

The VNC desktop is:      server:0
PORT=5900
connect_switch[S->C/4/1951]: Input is EOF.
connect_switch[C->S/4/1952]: Input is EOF.



I clearly dont understand the the rewrite rules and  the calling URL. theres probably  a lot more tha i dont understand as well .

thanks for any further pointers.

---

