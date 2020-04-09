# BGP-Router

__NOTE__: Cannot post this publicly unless requested to be viewed.
Email me at rkwong12@gmail.com to request.

_Created for CS3700, Networks and Distributed Systems with a partner._

This is a simple BGP router that keeps a forwarding table and forwards packets along to neighbors and peers if necessary.
It will also update neighbors by sending BGP protocol messages packed in a JSON format.
In sending or forwarding packets, it will look up the best possible path in this order:

1. The path with the highest "localpref".
2. The path with "selfOrigin" = true.
3. The path with the shortest "ASPath" wins.
4. The path with the best "origin" wins, were IGP > EGP > UNK. 
5. The path from the neighbor router with the lowest IP address.

IP addresses are stored in CIDR formats.

Functionality:

    - Accept route update messages from the BGP neighbors, and forward updates
    - Accept route revocation messages from the BGP neighbors, and forward revocations
    - Forward data packets
    - Return error messages in cases where a data packet cannot be delivered or are dropped
    - Coalesce forwarding table entries for networks that are adjacent and on the same port
    - Serialize the forwarding table so that it can be checked for correctness
    - Updated BGP neighbors for any path changes
    - Forwards or drops packets depending on peer relationships to the requested BGP neighbor

Command line syntax:
./router <asn> <ip_address>-<peer|prov|cust> [...]
  
Additionally, a net simulator was given to test the project. It is unmodified.

Command line syntax for net simulator:
$ ./sim [-h] [--test-dir <dir>] [--router <router>] <all|[milestone] file [...]>
