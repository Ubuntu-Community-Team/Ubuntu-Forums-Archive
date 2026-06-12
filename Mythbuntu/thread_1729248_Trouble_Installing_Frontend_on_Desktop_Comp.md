---
title: "Trouble Installing Frontend on Desktop Comp"
date: 2011-04-14
forum: Mythbuntu
---

### Post by phroman on 2011-04-14
Hello all, I'm having trouble trying to add a mythbuntu frontend to my existing Ubuntu desktop running 10.10

I have one computer which runs a frontend/backend.  I installed Mythbuntu Control Center on my 2nd computer via Synaptic.  Mythbuntu Control Center >  System Roles, I added MythTV Frontend. Starting MythTV Frontend, it couldn't connect to my backend, I exited, then it just hung when I restarted it, so I removed it and re-installed. 

When I try to start the Frontend now, it doesn't actually open a Frontend window, but System Monitor shows Mythfrontend and Mythfrontend.real running.  

Process Name:		Status:		Waiting Channel:
Mythfrontend		Sleeping  	do_wait
Mythfrontend.real	Sleeping	sk_wait_data

Here is the frontend log:
```

Starting mythfrontend.real..
2011-04-14 00:58:41.231 mythfrontend version: fixes/0.24 [v0.24-240-g1cfcb2b] www.mythtv.org
2011-04-14 00:58:41.231 Using runtime prefix = /usr
2011-04-14 00:58:41.231 Using configuration directory = /home/joe/.mythtv
2011-04-14 00:58:41.232 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-14 00:58:41.232 MediaRenderer::HttpServer Create Error
2011-04-14 00:58:41.233 Empty LocalHostName.
2011-04-14 00:58:41.233 Using localhost value of blackbox
2011-04-14 00:58:41.233 Testing network connectivity to '192.168.1.22'
2011-04-14 00:58:41.357 New DB connection, total: 1
Starting mythfrontend.real..
```

Don't know what the MediaRenderer::HttpServer Create Error is but google searches didn't lead me to anything unfortunately.  

In Synaptic Package Manager, I marked everything associate with myth for complete removal, re-installed, same thing.  Any ideas?  Thanks in advance!

---

### Post by klc5555 on 2011-04-15
To get a remote frontend working on a Ubuntu box, you strictly speaking need only 2 packages from synaptic: mythtv-common and mythtv-frontend.

Then, assuming your master backend server has been set up properly to accept remote database connections, you merely need to run "mythfrontend" from a prompt and fill in the configuration screen that pops up to tell the app where the backend server is and what is login, password, and PIN details are.

---

### Post by phroman on 2011-04-15
Hi klc5555, thanks for your reply. 

I went into Synaptic and marked everything Myth related for complete removal, rebooted, re-installed my desired myth packages, and all is well.  No idea what was causing the frontend window not to show up.  Configuring the master backend was no picnic, but it's done now..  Thanks!

---

