# 읽고말하기(look and say sequence) 알고리즘



[codesandbox link](https://codesandbox.io/embed/infallible-currying-p19cq)

```javascript
function sequencing(seq) {
  let temp = '';
  let len = seq.length;
  let count = 1;
  for (let i = 0; i < len; i++) {
    if (i + 1 !== len && seq.charAt(i) === seq.charAt(i + 1)) count++;
    else {
      temp = `${temp}${count}${seq.charAt(i)}`;
      count = 1;
    }
  }
  return temp;
}

function lookAndSaySeq(R, L) {
  if (L === 1) return R;

  for (let i = 0; i < L - 1; i++) {
    R = sequencing(R);
  }

  return R;
}

/** TEST */
let R = '1';
let L = 6;

for (let i = 0; i < 5; i++) {
  if (i > 0) {
    R = String(~~(Math.random() * (100 - 1) + 1));
    L = ~~(Math.random() * 25 + 1);
  }

  console.log(`** ${i + 1}번째 테스트케이스 **`);
  console.log(
    `Input\n${R}\n${L}\n\nOutput\n${lookAndSaySeq(R, L)
      .split("")
      .join(" ")}`
  );
}

```

