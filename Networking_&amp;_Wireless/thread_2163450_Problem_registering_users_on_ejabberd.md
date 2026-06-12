---
title: "Problem registering users on ejabberd"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by dougalcorn on 2013-07-18
[COLOR=#000000][FONT=Helvetica]I'm setting up an ejabberd server on an Ubuntu LTS 12.04. The community help wiki [says]("https://help.ubuntu.com/community/SettingUpJabberServer") I just need to:[/FONT][/COLOR]

[LIST=1]
[*]Install the package
[*]Edit the hosts configuration in ejabberd.cfg
[*]Update the admin user's definition
[*]Restart the server
[*]Register the admin user from the command line
[/LIST]
[COLOR=#000000][FONT=Helvetica]It's that last step that doesn't work. Here's what I get:[/FONT][/COLOR]

```

$ sudo ejabberdctl register ejabberd semperubisubsubi.org <password>
Can't register user [EMAIL="ejabberd@semperubisubsubi.org"]ejabberd@semperubisubsubi.org[/EMAIL] at node 'ejabberd@semperubisububi.org': not_allowed

```[COLOR=#000000][FONT=Helvetica]

There are a bunch of Google hits for "ejabber register not_allowed". I've spent about four or five hours reading them all. I still can't figure this out. I could really use some help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I know most of the posts talk about making sure you have agreement between your hostname, your hosts definition, and your node name. The Ubuntu init scripts are setup to use /etc/defaults/ejabberd to override some of the settings via environment variables. The only thing I have in there is this line:[/FONT][/COLOR]

```

ERLANG_NODE=ejabberd@semperubisububi.org

```[COLOR=#000000][FONT=Helvetica]

Which corresponds to my hostname:[/FONT][/COLOR]

```

$ hostname
semperubisububi.org
$ hostname -f
localhost
$ hostname -ssemperubisububi

```[COLOR=#000000][FONT=Helvetica]

I think that hostname -f is due to adding my FQDN to my /etc/hosts:[/FONT][/COLOR]

```

127.0.0.1  localhost susu semperubisububi.org

```[COLOR=#000000][FONT=Helvetica]

There are a bunch of Google hits for "ejabber register not_allowed". I've spent about four or five hours reading them all. I still can't figure this out. I could really use some help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I know most of the posts talk about making sure you have agreement between your hostname, your hosts definition, and your node name. The Ubuntu init scripts are setup to use /etc/defaults/ejabberd to override some of the settings via environment variables. The only thing I have in there is this line:[/FONT][/COLOR]

```

ERLANG_NODE=ejabberd@semperubisububi.org

```[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]
Here's what I think are the relevant sections of my ejabberd.cfg:
[/FONT][/COLOR]
```

{hosts, ["localhost", "semperubisububi.org"]}.
{access, max_user_sessions, [{10, all}]}.
{access, max_user_offline_messages, [{5000, admin}, {100, all}]}.
{access, local, [{allow, all}]}.
{access, c2s, [{deny, blocked},
               {allow, all}]}.

{access, c2s_shaper, [{none, admin},
                      {normal, all}]}.
{access, s2s_shaper, [{fast, all}]}.
{access, announce, [{allow, admin}]}.
{access, configure, [{allow, admin}]}.
{access, muc_admin, [{allow, admin}]}.
{access, muc, [{allow, all}]}.
{access, register, [{allow, all}]}.
{access, pubsub_createnode, [{allow, all}]}.

{acl, local, {user_regexp, ""}}.
{auth_method,  internal}.

```

I've created a gist with more notes (including my entire ejabberd.cfg): [https://gist.github.com/dougalcorn/6029329](https://gist.github.com/dougalcorn/6029329)

---

