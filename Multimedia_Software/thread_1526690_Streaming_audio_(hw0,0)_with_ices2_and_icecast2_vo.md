---
title: "Streaming audio (hw0,0) with ices2 and icecast2: volume far too low..."
date: 2010-07-08
forum: Multimedia Software
---

### Post by Pifilatakanemu on 2010-07-08
hey,
I achieved to create a stream of the audio output of my sound card thanks to ices2 and icecast2. i receive it with an internet radio device (NOXON). works alright, BUT the volume is far too low....

any suggestions?

Thanks!


ah, and there is a ~7sec delay... it's not to bad, but if it can be reduced, please tell me how.

---

### Post by cchhrriiss121212 on 2010-07-08
Tried alsamixer?

---

### Post by Pifilatakanemu on 2010-07-09
I started it already but I did not get that I could change the options through the F-keys.

I'll try to raise everything up to the top. I'll check tonight if it works.


Thanks!!!

---

### Post by Pifilatakanemu on 2010-07-09
The volume is higher now, but the quality is really bad.

I couldn't figure out why, so I'll post the ices-alsa.xml below

```
<?xml version="1.0"?>
<ices>

    <!-- run in background  -->
    <background>0</background>
    <!-- where logs go. -->
    <logpath>/var/log/ices</logpath>
    <logfile>ices.log</logfile>
    <!-- size in kilobytes -->
    <logsize>2048</logsize>
    <!-- 1=error, 2=warn, 3=infoa ,4=debug -->
    <loglevel>4</loglevel>
    <!-- logfile is ignored if this is set to 1 -->
    <consolelog>0</consolelog>

    <!-- optional filename to write process id to -->
    <!-- <pidfile>/home/ices/ices.pid</pidfile> -->

    <stream>
        <!-- metadata used for stream listing -->
        <metadata>
            <name>Example stream name</name>
            <genre>Example genre</genre>
            <description>A short description of your stream</description>
            <url>http://mysite.org</url>
        </metadata>

        <!--    Input module.

            This example uses the 'oss' module. It takes input from the
            OSS audio device (e.g. line-in), and processes it for live
            encoding.  -->
        <input>
            <module>alsa</module>
            <param name="rate">44100</param>
            <param name="channels">2</param>
            <param name="device">hw:0,0</param>
            <!-- Read metadata (from stdin by default, or -->
            <!-- filename defined below (if the latter, only on SIGUSR1) -->
            <param name="metadata">1</param>
            <param name="metadatafilename">test</param>
        </input>

        <!--    Stream instance.

            You may have one or more instances here.  This allows you to
            send the same input data to one or more servers (or to different
            mountpoints on the same server). Each of them can have different
            parameters. This is primarily useful for a) relaying to multiple
            independent servers, and b) encoding/reencoding to multiple
            bitrates.

            If one instance fails (for example, the associated server goes
            down, etc), the others will continue to function correctly.
            This example defines a single instance doing live encoding at
            low bitrate.  -->

        <instance>
            <!--    Server details.

                You define hostname and port for the server here, along
                with the source password and mountpoint.  -->

            <hostname>localhost</hostname>
            <port>8000</port>
            <password>hackme</password>
            <mount>/example1.ogg</mount>
            <yp>1</yp>   <!-- allow stream to be advertised on YP, default 0 -->

            <!--    Live encoding/reencoding:

                channels and samplerate currently MUST match the channels
                and samplerate given in the parameters to the oss input
                module above or the remsaple/downmix section below.  -->

            <encode>  
                <quality>10</quality>
                <samplerate>44100</samplerate>
                <channels>1</channels>
            </encode>

            <!-- stereo->mono downmixing, enabled by setting this to 1 -->
            <downmix>1</downmix>

            <!-- resampling.
            
                Set to the frequency (in Hz) you wish to resample to, -->
             
            <resample>
                <in-rate>44100</in-rate>
                <out-rate>22050</out-rate>
            </resample>
        </instance>

    </stream>
</ices>
```

with these settings I achieved 89kbps..


and this is the xml of icecast.

```
<icecast>
    <limits>
        <clients>100</clients>
        <sources>2</sources>
        <threadpool>5</threadpool>
        <queue-size>524288</queue-size>
        <client-timeout>30</client-timeout>
        <header-timeout>15</header-timeout>
        <source-timeout>10</source-timeout>
        <!-- If enabled, this will provide a burst of data when a client 
             first connects, thereby significantly reducing the startup 
             time for listeners that do substantial buffering. However,
             it also significantly increases latency between the source
             client and listening client.  For low-latency setups, you
             might want to disable this. -->
        <burst-on-connect>1</burst-on-connect>
        <!-- same as burst-on-connect, but this allows for being more
             specific on how much to burst. Most people won't need to
             change from the default 64k. Applies to all mountpoints  -->
        <burst-size>65535</burst-size>
    </limits>

    <authentication>
        <!-- Sources log in with username 'source' -->
        <source-password>hackme</source-password>
        <!-- Relays log in username 'relay' -->
        <relay-password>hackme</relay-password>

        <!-- Admin logs in with the username given below -->
        <admin-user>admin</admin-user>
        <admin-password>hackme</admin-password>
    </authentication>

    <!-- set the mountpoint for a shoutcast source to use, the default if not
         specified is /stream but you can change it here if an alternative is
         wanted or an extension is required
    <shoutcast-mount>/live.nsv</shoutcast-mount>
    -->

    <!-- Uncomment this if you want directory listings -->
    <!--
    <directory>
        <yp-url-timeout>15</yp-url-timeout>
        <yp-url>http://dir.xiph.org/cgi-bin/yp-cgi</yp-url>
    </directory>
     -->

    <!-- This is the hostname other people will use to connect to your server.
    It affects mainly the urls generated by Icecast for playlists and yp
    listings. -->
    <hostname>localhost</hostname>

    <!-- You may have multiple <listener> elements -->
    <listen-socket>
        <port>8000</port>
        <!-- <bind-address>127.0.0.1</bind-address> -->
        <!-- <shoutcast-mount>/stream</shoutcast-mount> -->
    </listen-socket>
    <!--
    <listen-socket>
        <port>8001</port>
    </listen-socket>
    -->

    <!--<master-server>127.0.0.1</master-server>-->
    <!--<master-server-port>8001</master-server-port>-->
    <!--<master-update-interval>120</master-update-interval>-->
    <!--<master-password>hackme</master-password>-->

    <!-- setting this makes all relays on-demand unless overridden, this is
         useful for master relays which do not have <relay> definitions here.
         The default is 0 -->
    <!--<relays-on-demand>1</relays-on-demand>-->

    <!--
    <relay>
        <server>127.0.0.1</server>
        <port>8001</port>
        <mount>/example.ogg</mount>
        <local-mount>/different.ogg</local-mount>
        <on-demand>0</on-demand>

        <relay-shoutcast-metadata>0</relay-shoutcast-metadata>
    </relay>
    -->

    <!-- Only define a <mount> section if you want to use advanced options,
         like alternative usernames or passwords
    <mount>
        <mount-name>/example-complex.ogg</mount-name>

        <username>othersource</username>
        <password>hackmemore</password>

        <max-listeners>2</max-listeners>
        <dump-file>/tmp/dump-example1.ogg</dump-file>
        <burst-size>65536</burst-size>
        <fallback-mount>/example2.ogg</fallback-mount>
        <fallback-override>1</fallback-override>
        <fallback-when-full>1</fallback-when-full>
        <intro>/example_intro.ogg</intro>
        <hidden>1</hidden>
        <no-yp>1</no-yp>
        <authentication type="htpasswd">
                <option name="filename" value="myauth"/>
                <option name="allow_duplicate_users" value="0"/>
        </authentication>
        <on-connect>/home/icecast/bin/stream-start</on-connect>
        <on-disconnect>/home/icecast/bin/stream-stop</on-disconnect>
    </mount>

    <mount>
        <mount-name>/auth_example.ogg</mount-name>
        <authentication type="url">
            <option name="mount_add"       value="http://myauthserver.net/notify_mount.php"/>
            <option name="mount_remove"    value="http://myauthserver.net/notify_mount.php"/>
            <option name="listener_add"    value="http://myauthserver.net/notify_listener.php"/>
            <option name="listener_remove" value="http://myauthserver.net/notify_listener.php"/>
        </authentication>
    </mount>

    -->

    <fileserve>1</fileserve>

    <paths>
		<!-- basedir is only used if chroot is enabled -->
        <basedir>/usr/share/icecast2</basedir>

        <!-- Note that if <chroot> is turned on below, these paths must both
             be relative to the new root, not the original root -->
        <logdir>/var/log/icecast2</logdir>
        <webroot>/usr/share/icecast2/web</webroot>
        <adminroot>/usr/share/icecast2/admin</adminroot>
        <!-- <pidfile>/usr/share/icecast2/icecast.pid</pidfile> -->

        <!-- Aliases: treat requests for 'source' path as being for 'dest' path
             May be made specific to a port or bound address using the "port"
             and "bind-address" attributes.
          -->
        <!--
        <alias source="/foo" dest="/bar"/>
          -->
        <!-- Aliases: can also be used for simple redirections as well,
             this example will redirect all requests for http://server:port/ to
             the status page
          -->
        <alias source="/" dest="/status.xsl"/>
    </paths>

    <logging>
        <accesslog>access.log</accesslog>
        <errorlog>error.log</errorlog>
        <!-- <playlistlog>playlist.log</playlistlog> -->
      	<loglevel>3</loglevel> <!-- 4 Debug, 3 Info, 2 Warn, 1 Error -->
      	<logsize>10000</logsize> <!-- Max size of a logfile -->
        <!-- If logarchive is enabled (1), then when logsize is reached
             the logfile will be moved to [error|access|playlist].log.DATESTAMP,
             otherwise it will be moved to [error|access|playlist].log.old.
             Default is non-archive mode (i.e. overwrite)
        -->
        <!-- <logarchive>1</logarchive> -->
    </logging>

    <security>
        <chroot>0</chroot>
        <!--
        <changeowner>
            <user>nobody</user>
            <group>nogroup</group>
        </changeowner>
        -->
    </security>
</icecast>
```

what can i do to improve the quality?

---

