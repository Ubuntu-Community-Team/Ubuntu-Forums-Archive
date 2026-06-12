---
title: "Audio Stream fail"
date: 2014-03-12
forum: Multimedia Software
---

### Post by fbugnon on 2014-03-12
Hi,

I'm trying to listen to an mp3 audio stream from a Brazilian site and I get this error under the application "Video":

[INDENT]An error occurred
The movie could not be read[/INDENT]

Same thing happens when I use VLC, but then I'm able to get some more details:

[INDENT]Your input can't be opened:
VLC is unable to open the MRL 'mms://stream.stj.jus.br/radio/14-02-24-AD-FATIMA UCHOA-CONEXAO-SUMULAS.mp3'. Check the log for details.
[/INDENT]

And the message (log):

[INDENT]main error: Write error: Broken pipe
access_mms error: failed to send command
main error: Write error: Broken pipe
access_mms error: failed to send command
access_mms error: cannot connect to server
access_mms error: error: HTTP/1.1 400 Bad Request
main error: open of `mms://stream.stj.jus.br/radio/14-02-24-AD-FATIMA UCHOA-CONEXAO-SUMULAS.mp3' failed[/INDENT]

This is the original link to the audio stream:
mms://stream.stj.jus.br/radio/14-02-24-AD-FATIMA UCHOA-CONEXAO-SUMULAS.mp3
(found on [this page]("http://www.stj.jus.br/portal_stj/publicacao/engine.wsp?tmp.area=398&tmp.texto=113588&utm_source=agencia&utm_medium=email&utm_campaign=pushsco") of a Brazilian Court, just in case)

I have no idea what the problem is, but I would really like being able to listen to this so...
Any help is greatly appreciated.

_______

Using Ubuntu 13.10 64bit

---

### Post by tgalati4 on 2014-03-12
The stream is not found at that address:

tgalati4@Mint14-Extensa ~ $ mplayer [http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA](http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA) UCHOA-CONEXAO-SUMULAS.mp3
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA](http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA).
Resolving stream.stj.jus.br for AF_INET6...

Couldn't resolve name for AF_INET6: stream.stj.jus.br
Resolving stream.stj.jus.br for AF_INET...
Connecting to server stream.stj.jus.br[189.125.176.223]: 80...

Server returned 404: Not Found
STREAM_ASF, URL: [http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA](http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA)
Resolving stream.stj.jus.br for AF_INET6...

Couldn't resolve name for AF_INET6: stream.stj.jus.br
Resolving stream.stj.jus.br for AF_INET...
Connecting to server stream.stj.jus.br[186.215.82.221]: 80...

Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving stream.stj.jus.br for AF_INET6...

Couldn't resolve name for AF_INET6: stream.stj.jus.br
Resolving stream.stj.jus.br for AF_INET...
Connecting to server stream.stj.jus.br[189.125.176.223]: 80...

Server returned 404: Not Found
No stream found to handle url [http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA](http://stream.stj.jus.br/radio/14-02-24-AD-FATIMA)


Playing UCHOA-CONEXAO-SUMULAS.mp3.
File not found: 'UCHOA-CONEXAO-SUMULAS.mp3'
Failed to open UCHOA-CONEXAO-SUMULAS.mp3.


Exiting... (End of file)

There is a space character in the filename, which will trip up the address.  Send an email to the court and ask them for the correct URL.

---

### Post by fbugnon on 2014-03-12
Hi tgalati4,

Thank you for your message:

> **tgalati4 said:**
> There is a space character in the filename, which will trip up the address.  Send an email to the court and ask them for the correct URL.

I've asked them to correct (I haven't notice the blank space this time) and I'll post back here to check.

But I might not sure this is the problem.
I've asked them many times before to correct video stream URLs, eliminating spaces and special characters (ç), but even after they did, I still have the problem.

For instance this video stream (where spaces where replaced by underlines):
mms://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv
(found on [this]("http://www.stj.jus.br/portal_stj/publicacao/engine.wsp?tmp.area=398&tmp.texto=113543&utm_source=agencia&utm_medium=email&utm_campaign=pushsco") page)
I still have the same problem.

---

### Post by tgalati4 on 2014-03-12
Nothing there either:

tgalati4@Mint14-Extensa /tmp $ wget [http://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv](http://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv)
--2014-03-12 16:31:41--  [http://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv](http://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv)
Resolving stream.stj.jus.br (stream.stj.jus.br)... 189.125.176.223, 186.215.82.221
Connecting to stream.stj.jus.br (stream.stj.jus.br)|189.125.176.223|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-03-12 16:31:42 ERROR 404: Not Found.

The stream may have a Windows-only codec:

tgalati4@Mint14-Extensa /tmp $ mplayer mms://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv.
STREAM_ASF, URL: mms://stream.stj.jus.br/tv/STJ_CIDADAO_276_YOUTUBE.wmv
Resolving stream.stj.jus.br for AF_INET6...

Couldn't resolve name for AF_INET6: stream.stj.jus.br
Resolving stream.stj.jus.br for AF_INET...
Connecting to server stream.stj.jus.br[186.215.82.221]: 1755...

Connected


MPlayer interrupted by signal 13 in module: open_stream
write error


MPlayer interrupted by signal 13 in module: open_stream

So, I'm not sure what the problem is.  With VLC and the message log set to "debug" it indicates no candidates for mms://--which usually means there is no codec to decode the stream.  Try it from a Windows machine with Windows Media Player.

---

