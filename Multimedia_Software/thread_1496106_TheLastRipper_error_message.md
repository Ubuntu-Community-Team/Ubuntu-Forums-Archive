---
title: "TheLastRipper error message"
date: 2010-05-28
forum: Multimedia Software
---

### Post by deegoire on 2010-05-28
[FONT=Comic Sans MS][SIZE=2]I'm trying to use TheLastRipper Linux port 1.4.0. It worked fine for a while, but after logging in, setting the tag, and tuning in, I keep getting the following pop up message:[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=2]
System.Net.WebException: Error getting response stream (ReadDone2): ReceiveFailure ---> System.Exception:    at System.Net.WebConnection.HandleError(WebExceptionStatus st, System.Exception e, System.String where)
   at System.Net.WebConnection.ReadDone(IAsyncResult result)
   at System.Net.Sockets.Socket+SocketAsyncResult.Complete()
   at System.Net.Sockets.Socket+Worker.Receive()
  at System.Net.WebConnection.HandleError (WebExceptionStatus st, System.Exception e, System.String where) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at LibLastRip.LastManager.StartRecording (Boolean newStation) [0x00000] [/SIZE][/FONT]

[FONT=Comic Sans MS][SIZE=2]I have TheLastRipper set to all the default settings. I am running Ubuntu 10.04 on an Acer Aspire One netbook. I have tried uninstalling the repository version and getting the program from the website with the same results.

Does anyone know what the problem is and have a suggestion on how to fix the problem?[/SIZE][/FONT]

---

### Post by tgalati4 on 2010-05-28
I use vagalume on Jaunty and it's working fine, so I don't think it's a stream change or that the site is down.

---

### Post by Ameades on 2010-06-19
I am also having the same problem.  Currently haven't found any solutions.

---

### Post by triwave on 2010-08-09
Did anybody ever find a solution for this problem? I see the same errors and would like the try the tool if there is a way to make it work in ubuntu 10.04 or even 9.10

---

