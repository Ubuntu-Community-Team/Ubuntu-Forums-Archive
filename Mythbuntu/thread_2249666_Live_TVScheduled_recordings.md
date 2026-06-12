---
title: "Live TV/Scheduled recordings"
date: 2014-10-23
forum: Mythbuntu
---

### Post by JeffNBNB on 2014-10-23
Using v0.27. I have a master backend/frontend and three frontend clients. 

I have had several instances where a person leaves one of the clients on Watch TV. All scheduled recordings for whatever channel is on Live TV will not record as the backend thinks that the recording already exists in Live TV. 

Is there any way to record a show, no matter what? There's got to be a workaround. 

Jeff

---

### Post by tgm4883 on 2014-10-23
> **JeffNBNB said:**
> Using v0.27. I have a master backend/frontend and three frontend clients. 

I have had several instances where a person leaves one of the clients on Watch TV. All scheduled recordings for whatever channel is on Live TV will not record as the backend thinks that the recording already exists in Live TV. 

Is there any way to record a show, no matter what? There's got to be a workaround. 

Jeff

There are three settings that might help you (all in the frontend I believe).

One is called "Live TV idle timeout (mins)". This will show a prompt every X minutes to verify someone is still watching Live TV. It is located in the frontend at Setup > Video > Playback on the first screen (General Playback (1/8))

The other two are called

Avoid conflicts between live TV and scheduled shows - Live TV will choose a tuner card that is less likely to have scheduled recordings rather than the best card available.	

Allow live TV to move scheduled shows - Scheduled recordings will be moved to the other cards (where possible), so that live TV will not be interrupted.	

I can't find these at the moment, I thought they were in the frontend but they may be in the backend.

---

