# Are your Sites Truly Isolated?

This organization holds the code to the NDSS'26 publication **Are your Sites Truly Isolated? Automatically Detecting Logic Bugs in Site Isolation Implementations**.
We implemented two new oracles for site isolation bypass vulnerabilities: The leak sanitizer detects cross-site data leaks, and the process sanitizer detects cross-site process reuse.
Both oracles are implemented as browser patches.

To trigger SI bypass bugs, we implemented a fuzzer utilizing WebIDL definitions to generate HTML/JS documents leading to diverse IPC interactions combined with a browser-integrated IPC fuzzer that randomly mutates IPC messages sent by the renderer, simulating a compromised renderer.

The paper can be found [here](https://www.ias.cs.tu-bs.de/publications/are_your_sites_truly_isolated.pdf).

```bib
@inproceedings{DreKleJoh26,
    title = {Are your Sites Truly Isolated? Automatically Detecting Logic Bugs in Site Isolation Implementations},
    author = {Jan Drescher AND David Klein AND Martin Johns},
    booktitle = {Proc. of the Network and Distributed System Security Symposium (NDSS)},
    year = {2026},
}
```

## Contents
- **[fuzzer](https://github.com/si-bypass-fuzzing/fuzzer):** The fuzzer that instruments the browser and generates HTML/JS documents
- **[chromium](https://github.com/si-bypass-fuzzing/chromium):** A fork of Chromium with our patches to add the IPC fuzzer and oracles
- **[gecko-dev](https://github.com/si-bypass-fuzzing/gecko-dev):** A fork of the legacy Firefox mirror with our patches to add the IPC fuzzer and oracles
- **[webidl2.js](https://github.com/si-bypass-fuzzing/webidl2.js):** A fork the W3C WebIDL parser, patched to work on the modified WebIDL grammars of Chromium and Firefox
- **[fuzzorigin](https://github.com/si-bypass-fuzzing/fuzzorigin):** A fork of the UXSS fuzzer Fuzzorigin, used in our evaluation
