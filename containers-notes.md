## Self-Mastery 101: Containers Technology ##
This contains all self-mastery notes on containers, starting with their histoy and latest advancements.

**Credits**: Linux Foundation course LFS253 is the source of knowledge.  

---

### Virtualization Fundamentals ###
1. These 3 linux OS based features are the building blocks of modern day containerisation. They have existed on a long time (> 20 years) as `OS Level Virtualization` techniques but only recent times did these features become more enriched that they are adapted for containers.  

1. The 3 most important features are `cgroups`, `namespaces` & `UnionFS`.

1. `cgroups` allow the limitation of memory, disk I/O, and network usage for a group of processes.  
In addition, cgroups may set usage quotas, and prioritize a process group to receive more CPU time or memory than other groups.  
Also, a group's resource usage can be measured for accounting and billing purposes, and its state can be controlled by freezing and restarting the group.

1. `Namespaces` may limit the visibility of cgroups, hostname, process IDs, IPC mechanisms, network interfaces and routes, users, and mounted file systems. To an isolated process running inside a namespace, a namespaced resource, such as the network, will appear as the process' own dedicated resource. Processes running inside a namespace are aware of any changes in the local namespaced system resources, however, such changes will not be visible to other processes or other namespaces.  
`Namespaces` isolate processes from one container to prevent them from modifying the hostname, network interfaces, or mounts for processes running in other containers. The processes isolated inside a container can only see system resources namespaced for that particular container. 

1. `UnionFS` allows the overlay of separate transparent file systems to produce an virtual single unified file system.
Several file systems, called branches, are virtually stacked, their contents appear to be merged, however, physically, they remain separate.  
The real physical separation, together with read-only and read-write access modes, help to prevent data corruption with the implementation of a `Copy-on-Write (CoW)` mechanism.  
`UniionFS` allows container images to be made at runtime, using heavy file linkages to main base image s source while allowing changes to be made to read writable file system.  

---

### Virtualization 101 ###
1. Operating system-level virtualization is a kernel's capability to allow creation and existence of multiple isolated environments, such as containers, on the same hosts, without a need to install a guest OS (unlike a full VM)

1. These containers or virtalizaed environments are limited by the kernel to its assigned devices. This separation allows programs to run in ther own assigned virual environment for better security and resource management.

1. It leverages a `CoW` mechanism type of stacked storage management model, shared by all containers.

1. Mechanisms implementing OS level virtualization are `chroot` (one of the oldest), `LXC` (Linux Containers), `Systemd-nspwan`

1. `chroot` - changing the root directory of a process and its children, to a virtual root, giving the impression the process has the real root directory of he OS, without the possibiliy of escaping to access the real root directory.

1. `LXC` introduced in 2008 on Linux systems. Leverages cgroups and chroot, with namespace isolation to limit resources and isolate from host OS.

1. `Systemd-nspawn` introdued in 2010 in Linux systems. Fully virtualize process tree, fiesystem, users, host and domain name. Processes cannot communicate aceoss containers. May run system services managed by `systemd`.

---
