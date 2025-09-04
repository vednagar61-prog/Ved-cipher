# Ved Cipher 🔐

The **Ved Cipher** is a substitution cipher invented by **Ved P. Nagar** on **4th September 2025**.  
It uses a unique pattern of alternating **previous** and **next** alphabet transformations.

---

## 🔑 Rules of the Ved Cipher
1. Take the original text.  
2. For the **1st letter**, replace it with the **previous alphabet** (A → Z, B → A, etc.).  
3. For the **2nd letter**, replace it with the **next alphabet** (A → B, Z → A, etc.).  
4. Keep repeating: **Previous → Next → Previous → Next...**

---

## 📝 Example
Text: `VED`  
- V → U (previous)  
- E → F (next)  
- D → C (previous)  

👉 **VED → UFC**

Another Example:  
`MY NAME IS VED` → `LZ MBLF HT UFC`

---

## 🔄 Decryption
To decrypt, just reverse the process:
- If a letter was shifted to **previous**, shift it **forward**.  
- If a letter was shifted to **next**, shift it **backward**.  

---

## 💻 Python Implementation
```python
def ved_encrypt(text: str) -> str:
    result = []
    for i, ch in enumerate(text.upper()):
        if not ch.isalpha():
            result.append(ch)
            continue
        if i % 2 == 0:  # Previous alphabet
            result.append(chr(((ord(ch) - 65 - 1) % 26) + 65))
        else:  # Next alphabet
            result.append(chr(((ord(ch) - 65 + 1) % 26) + 65))
    return "".join(result)

def ved_decrypt(text: str) -> str:
    result = []
    for i, ch in enumerate(text.upper()):
        if not ch.isalpha():
            result.append(ch)
            continue
        if i % 2 == 0:  # Was shifted to previous → shift forward
            result.append(chr(((ord(ch) - 65 + 1) % 26) + 65))
        else:  # Was shifted to next → shift backward
            result.append(chr(((ord(ch) - 65 - 1) % 26) + 65))
    return "".join(result)

# Example usage
print("Encrypt:", ved_encrypt("MY NAME IS VED"))
print("Decrypt:", ved_decrypt("LZ MBLF HT UFC"))
