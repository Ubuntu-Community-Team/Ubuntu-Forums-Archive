---
title: "Troubles with ServeToMe/StreamToMe to iPad"
date: 2010-08-12
forum: Multimedia Software
---

### Post by rosatimr on 2010-08-12
I am trying to use ServeToMe to stream audio and video to my iPad from my Ubuntu desktop (lucid Desktop).  I downloaded ServeToMe v307 from here [http://code.google.com/p/servetome/downloads/list](http://code.google.com/p/servetome/downloads/list) and followed the instructions to edit the config file.  Here is what my config file looks like

```
[ServeToMe]
username="user"
password="1234"
listenPort=9969
tempDir=/home/michael/stm/temp
execDir=/home/michael/stm/bin
directoryList=/home/michael/Downloads,/home/michael/Pictures/Photos,/data/media/arrivals,/data/media/movies
# extensionList=aif,m2ts,ts,flac,wmv,ogm,ogg,wma,m4a,vob,dif,dv,flv,asf,mp2,mp3,ac3,aac,mpeg4,mp4,m4v,mpeg,mkv,mpg,mov,gvi,avi
debugEnable=True
```

When I run ServeToMe this is what my terminal looks like:

```
12/08/10 17:07:13 Welcome to ServeToMe (3.07)
12/08/10 17:07:13 ====================
12/08/10 17:07:13 username="user"
12/08/10 17:07:13 password="1234"
12/08/10 17:07:13 listenPort=9969
12/08/10 17:07:13 tempDir=/home/michael/stm/temp
12/08/10 17:07:13 execDir=/home/michael/stm/bin
12/08/10 17:07:13 directoryList=['/home/michael/Downloads', '/home/michael/Pictures/Photos', '/data/media/arrivals', '/data/media/movies']
12/08/10 17:07:13 extensionList=('aif', 'm2ts', 'ts', 'flac', 'wmv', 'ogm', 'ogg', 'wma', 'm4a', 'vob', 'dif', 'dv', 'flv', 'asf', 'mp2', 'mp3', 'ac3', 'aac', 'mpeg4', 'mp4', 'm4v', 'mpeg', 'mkv', 'mpg', 'mov', 'gvi', 'avi')
12/08/10 17:07:13 debugEnable=True
12/08/10 17:07:13 started httpserver...
```

Then, on my iPad I open StreamToMe and "None Found" under local servers.  So I manually add the address and when I do that this is what my terminal returns:

```
12/08/10 17:07:13 Welcome to ServeToMe (3.07)
12/08/10 17:07:13 ====================
12/08/10 17:07:13 username="user"
12/08/10 17:07:13 password="1234"
12/08/10 17:07:13 listenPort=9969
12/08/10 17:07:13 tempDir=/home/michael/stm/temp
12/08/10 17:07:13 execDir=/home/michael/stm/bin
12/08/10 17:07:13 directoryList=['/home/michael/Downloads', '/home/michael/Pictures/Photos', '/data/media/arrivals', '/data/media/movies']
12/08/10 17:07:13 extensionList=('aif', 'm2ts', 'ts', 'flac', 'wmv', 'ogm', 'ogg', 'wma', 'm4a', 'vob', 'dif', 'dv', 'flv', 'asf', 'mp2', 'mp3', 'ac3', 'aac', 'mpeg4', 'mp4', 'm4v', 'mpeg', 'mkv', 'mpg', 'mov', 'gvi', 'avi')
12/08/10 17:07:13 debugEnable=True
12/08/10 17:07:13 started httpserver...
12/08/10 17:11:31 requestHandler(): Client:   192.168.1.106:61023
12/08/10 17:11:31 requestHandler(): Path:     /folders
12/08/10 17:11:31 sessionNew(): Created new session for client:9XaRTJVTjb5E
12/08/10 17:11:31 sessionNew(): SessionDir:/home/michael/stm/temp/session.9XaRTJVTjb5E
12/08/10 17:11:31 requestHandler(): New session 9XaRTJVTjb5E
12/08/10 17:11:31 doDirectory(): Shares: []
12/08/10 17:11:31 doDirectory(): Order: 0
12/08/10 17:11:31 doDirectory(): Sort: 4
12/08/10 17:11:31 doDirectory(): Heira: 0
12/08/10 17:11:31 doDirectory(): Out: [0] {"identifier": "0", "type": "folder", "name": "Downloads"}
12/08/10 17:11:31 doDirectory(): Out: [1] {"identifier": "1", "type": "folder", "name": "Photos"}
12/08/10 17:11:31 doDirectory(): Out: [2] {"identifier": "2", "type": "folder", "name": "arrivals"}
12/08/10 17:11:31 doDirectory(): Out: [3] {"identifier": "3", "type": "folder", "name": "movies"}
Alyssas-iPad.local - - [12/Aug/2010 17:11:31] "GET /folders HTTP/1.1" 200 -
```

I can see my folders on the left side of the iPad, but when I click on one of them, StreamToMe says "Connection Error.  Connection to server failed: lost network connection."  And my terminal on my desktop looks like this:

```
12/08/10 17:07:13 Welcome to ServeToMe (3.07)
12/08/10 17:07:13 ====================
12/08/10 17:07:13 username="user"
12/08/10 17:07:13 password="1234"
12/08/10 17:07:13 listenPort=9969
12/08/10 17:07:13 tempDir=/home/michael/stm/temp
12/08/10 17:07:13 execDir=/home/michael/stm/bin
12/08/10 17:07:13 directoryList=['/home/michael/Downloads', '/home/michael/Pictures/Photos', '/data/media/arrivals', '/data/media/movies']
12/08/10 17:07:13 extensionList=('aif', 'm2ts', 'ts', 'flac', 'wmv', 'ogm', 'ogg', 'wma', 'm4a', 'vob', 'dif', 'dv', 'flv', 'asf', 'mp2', 'mp3', 'ac3', 'aac', 'mpeg4', 'mp4', 'm4v', 'mpeg', 'mkv', 'mpg', 'mov', 'gvi', 'avi')
12/08/10 17:07:13 debugEnable=True
12/08/10 17:07:13 started httpserver...
12/08/10 17:11:31 requestHandler(): Client:   192.168.1.106:61023
12/08/10 17:11:31 requestHandler(): Path:     /folders
12/08/10 17:11:31 sessionNew(): Created new session for client:9XaRTJVTjb5E
12/08/10 17:11:31 sessionNew(): SessionDir:/home/michael/stm/temp/session.9XaRTJVTjb5E
12/08/10 17:11:31 requestHandler(): New session 9XaRTJVTjb5E
12/08/10 17:11:31 doDirectory(): Shares: []
12/08/10 17:11:31 doDirectory(): Order: 0
12/08/10 17:11:31 doDirectory(): Sort: 4
12/08/10 17:11:31 doDirectory(): Heira: 0
12/08/10 17:11:31 doDirectory(): Out: [0] {"identifier": "0", "type": "folder", "name": "Downloads"}
12/08/10 17:11:31 doDirectory(): Out: [1] {"identifier": "1", "type": "folder", "name": "Photos"}
12/08/10 17:11:31 doDirectory(): Out: [2] {"identifier": "2", "type": "folder", "name": "arrivals"}
12/08/10 17:11:31 doDirectory(): Out: [3] {"identifier": "3", "type": "folder", "name": "movies"}
Alyssas-iPad.local - - [12/Aug/2010 17:11:31] "GET /folders HTTP/1.1" 200 -
12/08/10 17:12:55 requestHandler(): Client:   192.168.1.106:61024
12/08/10 17:12:55 requestHandler(): Path:     /contents/Downloads
12/08/10 17:12:55 requestHandler(): Query:    sort=name&order=ascending&hierarchy=folder&images=yes
12/08/10 17:12:55 requestHandler(): Cookie:   9XaRTJVTjb5E
12/08/10 17:12:55 doDirectory(): Path: ['Downloads']
----------------------------------------
Exception happened during processing of request from ('192.168.1.106', 61024)
Traceback (most recent call last):
  File "/usr/lib/python2.6/SocketServer.py", line 281, in _handle_request_noblock
    self.process_request(request, client_address)
  File "/usr/lib/python2.6/SocketServer.py", line 307, in process_request
    self.finish_request(request, client_address)
  File "/usr/lib/python2.6/SocketServer.py", line 320, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.6/SocketServer.py", line 615, in __init__
    self.handle()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 329, in handle
    self.handle_one_request()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 323, in handle_one_request
    method()
  File "/home/michael/stm/stm.py", line 873, in do_GET
    doDirectory(client,self,url,options)
  File "/home/michael/stm/stm.py", line 732, in doDirectory
    fpath=buildPath(url)
  File "/home/michael/stm/stm.py", line 133, in buildPath
    fpath=directoryList[int(pathbits[0])]
ValueError: invalid literal for int() with base 10: 'Downloads'
----------------------------------------
12/08/10 17:12:55 requestHandler(): Client:   192.168.1.106:61025
12/08/10 17:12:55 requestHandler(): Path:     /contents/Downloads
12/08/10 17:12:55 requestHandler(): Query:    sort=name&order=ascending&hierarchy=folder&images=yes
12/08/10 17:12:55 requestHandler(): Cookie:   9XaRTJVTjb5E
12/08/10 17:12:55 doDirectory(): Path: ['Downloads']
----------------------------------------
Exception happened during processing of request from ('192.168.1.106', 61025)
Traceback (most recent call last):
  File "/usr/lib/python2.6/SocketServer.py", line 281, in _handle_request_noblock
    self.process_request(request, client_address)
  File "/usr/lib/python2.6/SocketServer.py", line 307, in process_request
    self.finish_request(request, client_address)
  File "/usr/lib/python2.6/SocketServer.py", line 320, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.6/SocketServer.py", line 615, in __init__
    self.handle()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 329, in handle
    self.handle_one_request()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 323, in handle_one_request
    method()
  File "/home/michael/stm/stm.py", line 873, in do_GET
    doDirectory(client,self,url,options)
  File "/home/michael/stm/stm.py", line 732, in doDirectory
    fpath=buildPath(url)
  File "/home/michael/stm/stm.py", line 133, in buildPath
    fpath=directoryList[int(pathbits[0])]
ValueError: invalid literal for int() with base 10: 'Downloads'
----------------------------------------
12/08/10 17:12:55 requestHandler(): Client:   192.168.1.106:61026
12/08/10 17:12:55 requestHandler(): Path:     /contents/Downloads
12/08/10 17:12:55 requestHandler(): Query:    sort=name&order=ascending&hierarchy=folder&images=yes
12/08/10 17:12:55 requestHandler(): Cookie:   9XaRTJVTjb5E
12/08/10 17:12:55 doDirectory(): Path: ['Downloads']
----------------------------------------
Exception happened during processing of request from ('192.168.1.106', 61026)
Traceback (most recent call last):
  File "/usr/lib/python2.6/SocketServer.py", line 281, in _handle_request_noblock
    self.process_request(request, client_address)
  File "/usr/lib/python2.6/SocketServer.py", line 307, in process_request
    self.finish_request(request, client_address)
  File "/usr/lib/python2.6/SocketServer.py", line 320, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.6/SocketServer.py", line 615, in __init__
    self.handle()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 329, in handle
    self.handle_one_request()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 323, in handle_one_request
    method()
  File "/home/michael/stm/stm.py", line 873, in do_GET
    doDirectory(client,self,url,options)
  File "/home/michael/stm/stm.py", line 732, in doDirectory
    fpath=buildPath(url)
  File "/home/michael/stm/stm.py", line 133, in buildPath
    fpath=directoryList[int(pathbits[0])]
ValueError: invalid literal for int() with base 10: 'Downloads'
----------------------------------------
```

What is the issue here?  ServeToMe on my Win7 laptop works fine with StreamToMe, but most of my media collection is on my Ubuntu Desktop.  Thanks for any help.

---

