---
title: "Mediatomb VLC Internet Radio Streaming"
date: 2010-04-24
forum: Multimedia Software
---

### Post by crash_l on 2010-04-24
Hi folks, hoping someone can help me out...  I'm trying to get Mediatomb to transcode (through VLC) Internet Radio Stream (shoutcast) to an mp3 stream.

If I use the VLC transcoding command on the command line, it works fine, creates the stream in the /tmp directory as my user.

When I hit this through UPNP client accessing Mediatomb, I see it creating the file in /tmp, however the permissions don't look quite right and the file is 0 bytes.  Eventually Mediatomb kills the processes and I get (obviously) invalid media type on my UPNP client.

Here's what I have in my profile section of config.xml (note I've hardcoded %in value for troubleshooting purposes):

 <transcode mimetype="audio/x-scpls" using="audio-common"/>

       <profile name="audio-common" enabled="yes" type="external">
        <mimetype>audio/mpeg</mimetype>
        <use-chunked-encoding>no</use-chunked-encoding>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <agent command="vlc" arguments="-I dummy 'http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957' --sout '#transcode{acodec=mp3,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=raw,dst=%out}'"/>
       <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>

Here's what I see in /tmp when attempting to run:
prw------- 1 mediatomb mediatomb       0 2010-04-24 11:01 mt_transcode_E56KBV
prw------- 1 mediatomb mediatomb       0 2010-04-24 11:01 mt_transcode_A90KBV

Here's what I see in the mediatomb.log file:
2010-04-24 11:01:16   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/online/object_id/23/res_id/none/pr_name/audio-common/tr/1, Path: (null)
2010-04-24 11:01:16   DEBUG: [../src/url_request_handler.cc:182] open(): start
2010-04-24 11:01:16   DEBUG: [../src/url_request_handler.cc:195] open(): full url (filename): /content/online/object_id/23/res_id/none/pr_name/audio-common/tr/1, parameters: object_id/23/res_id/none/pr_name/audio-common/tr/1
2010-04-24 11:01:16   DEBUG: [../src/url_request_handler.cc:231] open(): Online content url: [http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957](http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957)
2010-04-24 11:01:16   DEBUG: [../src/transcoding/transcode_ext_handler.cc:90] open(): start
2010-04-24 11:01:16   DEBUG: [../src/tools.cc:1039] normalizePath(): Normalizing path: /tmp//mt_transcode_E56KBV
2010-04-24 11:01:16   DEBUG: [../src/transcoding/transcode_ext_handler.cc:315] open(): creating fifo: /tmp/mt_transcode_E56KBV
2010-04-24 11:01:16    INFO: Arguments: -I dummy 'http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957' --sout '#transcode{acodec=mp3,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=raw,dst=%out}'
2010-04-24 11:01:16   DEBUG: [../src/process_executor.cc:77] ProcessExecutor(): Launched process vlc, pid: 15368
2010-04-24 11:01:16   DEBUG: [../src/process_executor.cc:71] ProcessExecutor(): Launching process: vlc
2010-04-24 11:01:16   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 10 -> 11
2010-04-24 11:01:16   DEBUG: [../src/io_handler_buffer_helper.cc:224] staticThreadProc(): starting buffer thread... thread: -1318339728
2010-04-24 11:01:22   DEBUG: [../src/process_io_handler.cc:258] read(): max timeouts, checking socket!
2010-04-24 11:01:26   DEBUG: [../src/web_callbacks.cc:72] create_request_handler(): Filename: /content/online/object_id/23/res_id/none/pr_name/audio-common/tr/1, Path: (null)
2010-04-24 11:01:26   DEBUG: [../src/url_request_handler.cc:182] open(): start
2010-04-24 11:01:26   DEBUG: [../src/url_request_handler.cc:195] open(): full url (filename): /content/online/object_id/23/res_id/none/pr_name/audio-common/tr/1, parameters: object_id/23/res_id/none/pr_name/audio-common/tr/1
2010-04-24 11:01:26   DEBUG: [../src/url_request_handler.cc:231] open(): Online content url: [http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957](http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957)
2010-04-24 11:01:26   DEBUG: [../src/transcoding/transcode_ext_handler.cc:90] open(): start
2010-04-24 11:01:26   DEBUG: [../src/tools.cc:1039] normalizePath(): Normalizing path: /tmp//mt_transcode_A90KBV
2010-04-24 11:01:26   DEBUG: [../src/transcoding/transcode_ext_handler.cc:315] open(): creating fifo: /tmp/mt_transcode_A90KBV
2010-04-24 11:01:26    INFO: Arguments: -I dummy 'http://yp.shoutcast.com/sbin/tunein-station.pls?id=8957' --sout '#transcode{acodec=mp3,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=raw,dst=%out}'
2010-04-24 11:01:26   DEBUG: [../src/process_executor.cc:77] ProcessExecutor(): Launched process vlc, pid: 15382
2010-04-24 11:01:26   DEBUG: [../src/process_executor.cc:71] ProcessExecutor(): Launching process: vlc
2010-04-24 11:01:26   DEBUG: [../src/io_handler_buffer_helper.cc:224] staticThreadProc(): starting buffer thread... thread: -1259865232
2010-04-24 11:01:28   DEBUG: [../src/process_io_handler.cc:258] read(): max timeouts, checking socket!
2010-04-24 11:01:32   DEBUG: [../src/process_io_handler.cc:258] read(): max timeouts, checking socket!
2010-04-24 11:01:34   DEBUG: [../src/process_io_handler.cc:258] read(): max timeouts, checking socket!
2010-04-24 11:01:34   DEBUG: [../src/io_handler_buffer_helper.cc:227] staticThreadProc(): buffer thread shut down. thread: -1318339728
2010-04-24 11:01:34   DEBUG: [../src/process_io_handler.cc:438] close(): terminating process, closing /tmp/mt_transcode_E56KBV
2010-04-24 11:01:34   DEBUG: [../src/process.cc:151] kill_proc(): KILLING TERM PID: 15368
2010-04-24 11:01:35   DEBUG: [../src/process_io_handler.cc:438] close(): terminating process, closing /tmp/mt_transcode_E56KBV
2010-04-24 11:01:38   DEBUG: [../src/process_io_handler.cc:258] read(): max timeouts, checking socket!
2010-04-24 11:01:44   DEBUG: [../src/process_io_handler.cc:258] read(): max timeouts, checking socket!
2010-04-24 11:01:44   DEBUG: [../src/io_handler_buffer_helper.cc:227] staticThreadProc(): buffer thread shut down. thread: -1259865232
2010-04-24 11:01:44   DEBUG: [../src/process_io_handler.cc:438] close(): terminating process, closing /tmp/mt_transcode_A90KBV
2010-04-24 11:01:44   DEBUG: [../src/process.cc:151] kill_proc(): KILLING TERM PID: 15382
2010-04-24 11:01:45   DEBUG: [../src/process_io_handler.cc:438] close(): terminating process, closing /tmp/mt_transcode_A90KBV


Anyone with similar experience?  Any thoughts?
Thanks in advance for any help folks can provide.

---

### Post by cweiske on 2012-01-10
Same question asked on sourceforge: [http://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/3687002](http://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/3687002)

---

